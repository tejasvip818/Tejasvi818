*** Settings ***
Library    Browser

*** Test Cases ***
Register New User
    New Browser    chromium    headless=False
    New Page    https://www.automationexercise.com/
    Click    text=Signup / Login
