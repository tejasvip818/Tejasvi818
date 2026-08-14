*** Settings ***
Library    SeleniumLibrary
Resource   locators.robot


*** Keywords ***

Open Automation Exercise
    Open Browser    https://automationexercise.com/    Chrome
    Maximize Browser Window

Click Signup Login
    Click Element    ${SIGNUP_LOGIN}

Enter Signup Details
    [Arguments]    ${name}    ${email}
    Input Text    ${SIGNUP_NAME}    ${name}
    Input Text    ${SIGNUP_EMAIL}    ${email}
    Click Element    ${SIGNUP_BUTTON}

Enter Account Information
    [Arguments]    ${password}
    Click Element    ${GENDER_MALE}
    Input Text    ${PASSWORD}    ${password}
    Select From List By Value    ${DAY}    10
    Select From List By Label    ${MONTH}    May
    Select From List By Value    ${YEAR}    1995

Enter Address Information
    Input Text    ${FIRST_NAME}       Tejasvi
    Input Text    ${LAST_NAME}        Pratap
    Input Text    ${ADDRESS}          Bangalore
    Select From List By Label    ${COUNTRY}    India
    Input Text    ${STATE}            Karnataka
    Input Text    ${CITY}             Bangalore
    Input Text    ${ZIPCODE}          560001
    Input Text    ${MOBILE_NUMBER}    9876543210

Create Account
    Click Element    ${CREATE_ACCOUNT}
