*** Variables ***
# ===== HOME PAGE =====
${link_signupLogin}       xpath://a[normalize-space()='Signup / Login']
${link_products}          xpath://a[normalize-space()='Products']
${link_cart}              xpath:(//a[@href='/view_cart'])[1]

# ===== NEW USER SIGNUP =====
${lbl_newUserSignup}      xpath://h2[normalize-space()='New User Signup!']
${txt_signupName}         xpath://input[@data-qa='signup-name']
${txt_signupEmail}        xpath://input[@data-qa='signup-email']
${btn_signup}             xpath://button[normalize-space()='Signup']

# ===== ENTER ACCOUNT INFORMATION =====
${lbl_accountInfo}        xpath://b[normalize-space()='Enter Account Information']
${rdo_titleMr}            xpath://input[@id='id_gender1']
${txt_password}           xpath://input[@id='password']
${drp_days}               id:days
${drp_months}             id:months
${drp_years}              id:years
${chk_newsletter}         xpath://input[@id='newsletter']
${chk_specialOffers}      xpath://input[@id='optin']

# ===== ADDRESS INFORMATION =====
${txt_firstName}          xpath://input[@id='first_name']
${txt_lastName}           xpath://input[@id='last_name']
${txt_company}            xpath://input[@id='company']
${txt_address1}           xpath://input[@id='address1']
${txt_address2}           xpath://input[@id='address2']
${drp_country}            id:country
${txt_state}              xpath://input[@id='state']
${txt_city}               xpath://input[@id='city']
${txt_postCode}           xpath://input[@id='zipcode']
${txt_mobileNumber}       xpath://input[@id='mobile_number']
${btn_createAccount}      xpath://button[normalize-space()='Create Account']

# ===== ACCOUNT CREATED =====
${lbl_accountCreated}     xpath://b[normalize-space()='Account Created!']
${btn_continue}           xpath://a[@data-qa='continue-button']
${lbl_loggedInAs}         xpath://a[contains(text(),'Logged in as')]

# ===== PRODUCTS / ADD TO CART =====
${lbl_allProducts}        xpath://h2[normalize-space()='All Products']
${btn_addProduct1}        xpath:(//a[@data-product-id='1'])[1]
${btn_addProduct2}        xpath:(//a[@data-product-id='2'])[1]
${lbl_addedModal}         xpath://h4[normalize-space()='Added!']
${btn_continueShopping}   xpath://button[normalize-space()='Continue Shopping']
${link_viewCart}          xpath://u[normalize-space()='View Cart']

# ===== CART PAGE =====
${tbl_cartInfo}           xpath://table[@id='cart_info_table']
${link_proceedCheckout}   xpath://a[normalize-space()='Proceed To Checkout']

# ===== CHECKOUT PAGE =====
${lbl_addressDetails}     xpath://h2[normalize-space()='Address Details']
${lbl_reviewOrder}        xpath://h2[normalize-space()='Review Your Order']
${txt_orderComment}       xpath://textarea[@name='message']
${btn_placeOrder}         xpath://a[normalize-space()='Place Order']

# ===== PAYMENT PAGE =====
${txt_nameOnCard}         xpath://input[@name='name_on_card']
${txt_cardNumber}         xpath://input[@name='card_number']
${txt_cvc}                xpath://input[@name='cvc']
${txt_expiryMonth}        xpath://input[@name='expiry_month']
${txt_expiryYear}         xpath://input[@name='expiry_year']
${btn_payConfirm}         xpath://button[@data-qa='pay-button']

# ===== ORDER CONFIRMATION =====
${lbl_orderPlaced}        xpath://b[normalize-space()='Order Placed!']
${lbl_orderConfirmed}     xpath://p[contains(text(),'Congratulations')]
${btn_downloadInvoice}    xpath://a[normalize-space()='Download Invoice']
${btn_continueOrder}      xpath://a[@data-qa='continue-button']

# ===== DELETE ACCOUNT / LOGOUT =====
${link_deleteAccount}     xpath://a[normalize-space()='Delete Account']
${lbl_accountDeleted}     xpath://b[normalize-space()='Account Deleted!']
${link_logout}            xpath://a[normalize-space()='Logout']
