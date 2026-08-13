*** Settings ***
Library    Browser

*** Test Cases ***
Register New User
    New Browser    chromium    headless=False
    New Page    https://www.automationexercise.com/    wait_until=domcontentloaded
    Click    text=Signup / Login
