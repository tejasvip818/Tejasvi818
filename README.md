*** Settings ***
Library    SeleniumLibrary

*** Test Cases ***
Registration Test
    Open Browser    https://automationexercise.com/    Chrome
    Maximize Browser Window
    Sleep    3s
    Close Browser
