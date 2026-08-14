*** Variables ***

# Home / Login
${SIGNUP_LOGIN}          xpath=//a[contains(text(),'Signup / Login')]

# Signup
${SIGNUP_NAME}            xpath=//input[@data-qa='signup-name']
${SIGNUP_EMAIL}           xpath=//input[@data-qa='signup-email']
${SIGNUP_BUTTON}          xpath=//button[@data-qa='signup-button']

# Account Information
${GENDER_MALE}            xpath=//input[@id='id_gender1']
${PASSWORD}               xpath=//input[@id='password']
${DAY}                    xpath=//select[@id='days']
${MONTH}                  xpath=//select[@id='months']
${YEAR}                   xpath=//select[@id='years']

# Address Information
${FIRST_NAME}             xpath=//input[@id='first_name']
${LAST_NAME}              xpath=//input[@id='last_name']
${ADDRESS}                xpath=//input[@id='address1']
${COUNTRY}                xpath=//select[@id='country']
${STATE}                  xpath=//input[@id='state']
${CITY}                   xpath=//input[@id='city']
${ZIPCODE}                xpath=//input[@id='zipcode']
${MOBILE_NUMBER}          xpath=//input[@id='mobile_number']

# Create Account
${CREATE_ACCOUNT}         xpath=//button[@data-qa='create-account']
