*** Settings ***
Library     SeleniumLibrary
Resource    ../Resource/loginkeywords.robot

*** Variables ***
${Browser}    chrome
${SiteUrl}    https://www.automationexercise.com/

*** Test Cases ***
LoginTest
    Open my Browser    ${SiteUrl}    ${Browser}
    Click SignupLogin Link
    Enter Login Email       tejasvi9911@yopmail.com
    Enter Login Password    Test@1234
    Click Login Button
    Verify Login Successful
    Click Logout
    Close my Browser

InvalidLoginTest
    Open my Browser    ${SiteUrl}    ${Browser}
    Click SignupLogin Link
    Enter Login Email       galat@yopmail.com
    Enter Login Password    GalatPassword
    Click Login Button
    Verify Login Failed
    Close my Browser
