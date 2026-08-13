*** Settings ***
Library    Browser

*** Test Cases ***
Register New User
    New Browser    chromium    headless=False
    New Page    https://www.automationexercise.com/    wait_until=domcontentloaded
    Click    text=Signup / Login
    Fill Text    input[data-qa="signup-name"]    Tejas
    Fill Text    input[data-qa="signup-email"]    tejas12345@gmail.com
