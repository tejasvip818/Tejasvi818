*** Settings ***
Library     SeleniumLibrary
Resource    ../pageobject/variable.robot


*** Keywords ***
# ---------- BROWSER ----------
Open my Browser
    [Arguments]    ${SiteUrl}    ${Browser}
    Open Browser    ${SiteUrl}    ${Browser}
    Maximize Browser Window
    Sleep    2s

Close my Browser
    Close Browser

# ---------- REGISTRATION ----------
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

Enter Address Information
    Input Text    ${txt_firstName}       Tejasvi
    Input Text    ${txt_lastName}        Kumar
    Input Text    ${txt_company}         Capgemini
    Input Text    ${txt_address1}        MG Road
    Input Text    ${txt_address2}        Near Metro
    Select From List By Label    ${drp_country}    India
    Input Text    ${txt_state}           Karnataka
    Input Text    ${txt_city}            Bengaluru
    Input Text    ${txt_postCode}        560001
    Input Text    ${txt_mobileNumber}    9876543210

Click Create Account
    Click Button    ${btn_createAccount}
    Sleep    3s

Verify Account Created
    Page Should Contain Element    ${lbl_accountCreated}
    Click Element    ${btn_continue}
    Sleep    2s

Verify User Is LoggedIn
    Page Should Contain Element    ${lbl_loggedInAs}

# ---------- ADD TO CART ----------
Click Products Link
    Click Element    ${link_products}
    Sleep    3s
    Page Should Contain Element    ${lbl_allProducts}

Add First Product To Cart
    Click Element    ${btn_addProduct1}
    Sleep    2s
    Page Should Contain Element    ${lbl_addedModal}

Click Continue Shopping
    Click Element    ${btn_continueShopping}
    Sleep    2s

Add Second Product To Cart
    Click Element    ${btn_addProduct2}
    Sleep    2s
    Page Should Contain Element    ${lbl_addedModal}

Click View Cart
    Click Element    ${link_viewCart}
    Sleep    3s

Verify Cart Page
    Page Should Contain Element    ${tbl_cartInfo}

# ---------- CHECKOUT ----------
Click Proceed To Checkout
    Click Element    ${link_proceedCheckout}
    Sleep    3s

Verify Address And Order
    Page Should Contain Element    ${lbl_addressDetails}
    Page Should Contain Element    ${lbl_reviewOrder}

Enter Order Comment
    [Arguments]    ${comment}
    Input Text    ${txt_orderComment}    ${comment}

Click Place Order
    Click Element    ${btn_placeOrder}
    Sleep    3s

# ---------- PAYMENT ----------
Enter Payment Details
    [Arguments]    ${nameOnCard}    ${cardNo}    ${cvc}    ${month}    ${year}
    Input Text    ${txt_nameOnCard}     ${nameOnCard}
    Input Text    ${txt_cardNumber}     ${cardNo}
    Input Text    ${txt_cvc}            ${cvc}
    Input Text    ${txt_expiryMonth}    ${month}
    Input Text    ${txt_expiryYear}     ${year}

Click Pay And Confirm Order
    Click Element    ${btn_payConfirm}
    Sleep    5s

Verify Order Confirmed
    Page Should Contain Element    ${lbl_orderPlaced}
    Page Should Contain Element    ${lbl_orderConfirmed}

Click Continue After Order
    Click Element    ${btn_continueOrder}
    Sleep    2s

# ---------- CLEANUP ----------
Delete Account
    Click Element    ${link_deleteAccount}
    Sleep    3s
    Page Should Contain Element    ${lbl_accountDeleted}
    Click Element    ${btn_continue}
    Sleep    2s

Click Logout
    Click Element    ${link_logout}
    Sleep    2s
