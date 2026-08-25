*** Settings ***
Library     SeleniumLibrary
Resource    ../pageobject/locators.robot

*** Keywords ***
Open my Browser
    [Arguments]    ${SiteUrl}    ${Browser}
    Open Browser    ${SiteUrl}    ${Browser}
    Maximize Browser Window
    Sleep    2s

Click SignupLogin Link
    Click Element    ${link_signupLogin}
    Sleep    2s

Enter Signup Name
    [Arguments]    ${name}
    Input Text    ${txt_signupName}    ${name}

Enter Signup Email
    [Arguments]    ${email}
    Input Text    ${txt_signupEmail}    ${email}

Click Signup Button
    Click Button    ${btn_signup}
    Sleep    3s

Select Title
    Click Element    ${rdo_titleMr}

Enter Password
    [Arguments]    ${password}
    Input Text    ${txt_password}    ${password}

Select DateOfBirth
    [Arguments]    ${day}    ${month}    ${year}
    Select From List By Label    ${drp_days}      ${day}
    Select From List By Label    ${drp_months}    ${month}
    Select From List By Label    ${drp_years}     ${year}

Select Newsletter And Offers
    Select Checkbox    ${chk_newsletter}
    Select Checkbox    ${chk_specialOffers}

Enter FirstName
    [Arguments]    ${firstName}
    Input Text    ${txt_firstName}    ${firstName}

Enter LastName
    [Arguments]    ${lastName}
    Input Text    ${txt_lastName}    ${lastName}

Enter Company
    [Arguments]    ${company}
    Input Text    ${txt_company}    ${company}

Enter Address1
    [Arguments]    ${address1}
    Input Text    ${txt_address1}    ${address1}

Enter Address2
    [Arguments]    ${address2}
    Input Text    ${txt_address2}    ${address2}

Select Country
    [Arguments]    ${country}
    Select From List By Label    ${drp_country}    ${country}

Enter State
    [Arguments]    ${state}
    Input Text    ${txt_state}    ${state}

Enter City
    [Arguments]    ${city}
    Input Text    ${txt_city}    ${city}

Enter PostCode
    [Arguments]    ${postCode}
    Input Text    ${txt_postCode}    ${postCode}

Enter MobileNumber
    [Arguments]    ${mobile}
    Input Text    ${txt_mobileNumber}    ${mobile}

Click Create Account
    Click Button    ${btn_createAccount}
    Sleep    3s

Verify Account Created
    Page Should Contain Element    ${lbl_accountCreated}
    Click Element    ${btn_continue}
    Sleep    2s

Click Logout
    Click Element    ${link_logout}
    Sleep    2s

Close my Browser
    Close Browser
