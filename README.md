*** Settings ***
Library    Browser

*** Test Cases ***
Register New User
    New Browser    chromium    headless=False
    Set Browser Timeout    30 seconds
    New Page    https://www.automationexercise.com/
