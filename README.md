*** Variables ***
# Home Page
${link_signupLogin}       xpath://a[normalize-space()='Signup / Login']

# New User Signup box
${lbl_newUserSignup}      xpath://h2[normalize-space()='New User Signup!']
${txt_signupName}         xpath://input[@data-qa='signup-name']
${txt_signupEmail}        xpath://input[@data-qa='signup-email']
${btn_signup}             xpath://button[normalize-space()='Signup']
${lbl_emailExistError}    xpath://p[normalize-space()='Email Address already exist!']

# Login box
${lbl_loginHeader}        xpath://h2[normalize-space()='Login to your account']
${txt_loginEmail}         xpath://input[@data-qa='login-email']
${txt_loginPassword}      xpath://input[@data-qa='login-password']
${btn_login}              xpath://button[normalize-space()='Login']
${lbl_loginError}         xpath://p[normalize-space()='Your email or password is incorrect!']

# Enter Account Information
${rdo_titleMr}            xpath://input[@id='id_gender1']
${txt_password}           xpath://input[@id='password']
${drp_days}               id:days
${drp_months}             id:months
${drp_years}              id:years
${chk_newsletter}         xpath://input[@id='newsletter']
${chk_specialOffers}      xpath://input[@id='optin']

# Address Information
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

# After Signup / Login
${lbl_accountCreated}     xpath://h2[@data-qa='account-created']
${btn_continue}           xpath://a[normalize-space()='Continue']
${lbl_loggedInAs}         xpath://a[contains(text(),'Logged in as')]
${link_logout}            xpath://a[normalize-space()='Logout']
