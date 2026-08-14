*** Settings ***
Resource    ../resources/keywords.robot

Test Setup       Open Automation Exercise
Test Teardown    Close All Browsers


*** Test Cases ***
Registration With Valid Details
    Click Signup Login

    Enter Signup Details
    ...    Tejasvi
    ...    tejasvi987654321@gmail.com

    Page Should Contain    Enter Account Information

    Enter Account Information
    ...    Test@12345

    Enter Address Information

    Create Account

    Page Should Contain    ACCOUNT CREATED!
