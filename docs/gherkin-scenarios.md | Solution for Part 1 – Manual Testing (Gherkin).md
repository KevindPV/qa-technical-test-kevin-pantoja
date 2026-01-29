# 🧪 Manual Test Scenarios (Gherkin) – User Registration

This document contains the solution for **Part 1 – Manual Testing (Gherkin)** and includes 10 test scenarios written in Gherkin format:

- 5 Positive scenarios
- 5 Negative scenarios

---

## ✅ Positive Scenarios (5)

```gherkin

Feature: User Registration
  As a new user
  I want to register using the form
  So that I can create an account

  Background:
    Given the user is on the registration form

  Scenario: Successful registration with valid data
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.pantoja@example.com" in "Email"
    And the user enters "123456789" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should be created successfully
    And a success confirmation message should be displayed

  Scenario: Successful registration with full name containing multiple words
    When the user enters "Kevin Andres Pantoja Ruiz" in "Full name"
    And the user enters "kevin.multi@example.com" in "Email"
    And the user enters "987654321" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should be created successfully

  Scenario: Successful registration when email contains uppercase letters
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "KEVIN.PANTOJA@EXAMPLE.COM" in "Email"
    And the user enters "1122334455" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should be created successfully
    And the email should be stored in a normalized format (lowercase)

  Scenario: Successful registration allowing common special characters in password
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.special@example.com" in "Email"
    And the user enters "2233445566" in "Identification number"
    And the user enters "Str0ng#Pass!" in "Password"
    And the user enters "Str0ng#Pass!" in "Confirm password"
    And the user clicks "Register"
    Then the account should be created successfully

  Scenario: Successful registration with leading and trailing spaces trimmed in full name
    When the user enters "  Kevin Pantoja  " in "Full name"
    And the user enters "kevin.trim@example.com" in "Email"
    And the user enters "3344556677" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should be created successfully
    And the full name should be stored without leading or trailing spaces


## ❌ Negative Scenarios (5)

Feature: User Registration

  Background:
    Given the user is on the registration form

  Scenario: Registration fails when required field "Email" is empty
    When the user enters "Kevin Pantoja" in "Full name"
    And the user leaves "Email" empty
    And the user enters "123456789" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should not be created
    And an error message should be displayed indicating "Email is required"

  Scenario: Registration fails with invalid email format
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.pantoja@" in "Email"
    And the user enters "123456789" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should not be created
    And an error message should be displayed indicating "Invalid email format"

  Scenario: Registration fails when password and confirm password do not match
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.mismatch@example.com" in "Email"
    And the user enters "123456789" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "DifferentP4ss!" in "Confirm password"
    And the user clicks "Register"
    Then the account should not be created
    And an error message should be displayed indicating "Passwords do not match"

  Scenario: Registration fails when identification number contains non-numeric characters
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.id@example.com" in "Email"
    And the user enters "12A45-678" in "Identification number"
    And the user enters "P4ssw0rd!" in "Password"
    And the user enters "P4ssw0rd!" in "Confirm password"
    And the user clicks "Register"
    Then the account should not be created
    And an error message should be displayed indicating "Identification number must be numeric"

  Scenario: Registration fails when password does not meet minimum complexity
    When the user enters "Kevin Pantoja" in "Full name"
    And the user enters "kevin.weak@example.com" in "Email"
    And the user enters "123456789" in "Identification number"
    And the user enters "12345" in "Password"
    And the user enters "12345" in "Confirm password"
    And the user clicks "Register"
    Then the account should not be created
    And an error message should be displayed indicating "Password does not meet requirements"

