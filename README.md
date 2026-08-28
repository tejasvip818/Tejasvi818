*** Settings ***
Library     SeleniumLibrary
Resource    ../Resource/orderkeywords.robot


*** Variables ***
${Browser}      chrome
${SiteUrl}      https://www.automationexercise.com/
${UserEmail}    tejasvi2808@yopmail.com
${Password}     Test@1234


*** Test Cases ***
PlaceOrderEndToEndTest
    [Documentation]    Registration -> Add to Cart -> Place Order -> Confirmation

    # ===== STEP 1 : Browser open =====
    Open my Browser    ${SiteUrl}    ${Browser}

    # ===== STEP 2 : Registration =====
    Click SignupLogin Link
    Enter Signup Name     Tejasvi
    Enter Signup Email    ${UserEmail}
    Click Signup Button
    Select Title
    Enter Password        ${Password}
    Select DateOfBirth    18    May    2000
    Select Newsletter And Offers
    Enter Address Information
    Click Create Account
    Verify Account Created
    Verify User Is LoggedIn

    # ===== STEP 3 : Add products to cart =====
    Click Products Link
    Add First Product To Cart
    Click Continue Shopping
    Add Second Product To Cart
    Click View Cart
    Verify Cart Page

    # ===== STEP 4 : Checkout =====
    Click Proceed To Checkout
    Verify Address And Order
    Enter Order Comment    Please deliver before 6 PM
    Click Place Order

    # ===== STEP 5 : Payment =====
    Enter Payment Details    Tejasvi Kumar    4111111111111111    311    05    2030
    Click Pay And Confirm Order

    # ===== STEP 6 : Order confirmation =====
    Verify Order Confirmed

    # ===== STEP 7 : Cleanup =====
    Delete Account
    Close my Browser
