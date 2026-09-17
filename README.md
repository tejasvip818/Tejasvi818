#*********************************************************************
# Script Name      : ES4_OTC_SE_001_Verify_Login_Web
# Description      : Verifies login with valid credentials
# Author           : Tejasvi
# Created on       : 09/17/2026
# Modified by      :
# Modified on      :
# Input Parameter  : ${EMAIL}, ${PASSWORD}
# Output Parameter : NA
# Comments         : ADO Test Case 9990001
#*********************************************************************

*** Settings ***
Documentation    Verify login with valid credentials

Resource         ../../steps/login_steps.robot

Test Setup       Open Main Page Using Chrome Browser
Test Teardown    Close Main Browser

Force Tags       sanity    otc


*** Test Cases ***
Verify Login With Valid Credentials
    [Documentation]    ADO Test Case 9990001
    Navigate To Login Page
    Logon To Application
    Verify Login Successful
