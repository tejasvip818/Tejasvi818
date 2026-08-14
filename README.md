*** Settings ***
Resource    ../resources/keywords.robot

Test Setup       Open Automation Exercise
Test Teardown    Close All Browsers


*** Test Cases ***

Login With Valid Credentials
    Click Signup Login

    Wait Until Page Contains    Login to your account    10s

    Login With Valid Credentials
    ...    YOUR_REGISTERED_EMAIL
    ...    YOUR_REGISTERED_PASSWORD

    Page Should Contain    Logged in as
