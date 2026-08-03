from playwright.sync_api import sync_playwright
import time

def test_complete_signup():
    with sync_playwright() as p:
        browser = p.chromium.launch(headless=False, slow_mo=500)  # slow_mo se dheere-dheere dikhega
        page = browser.new_page()
        page.goto("https://automationexercise.com")

        # Step 1: Signup/Login page pe jao
        page.get_by_role("link", name="Signup / Login").click()

        # Step 2: Mini signup form fill karo (Name + Email)
        page.get_by_role("textbox", name="Name").fill("Tejasvi")
        page.locator("form").filter(has_text="Signup").get_by_placeholder("Email Address").fill("tejasvi123test@gmail.com")
        page.get_by_role("button", name="Signup").click()

        # Step 3: Account Information page — sab fields fill karo
        page.locator("#id_gender1").check()  # Mr. radio button
        page.get_by_role("textbox", name="Password *").fill("Test@1234")

        # Date of Birth
        page.locator("#days").select_option("15")
        page.locator("#months").select_option("5")
        page.locator("#years").select_option("2000")

        # Checkboxes (optional)
        page.get_by_role("checkbox", name="Sign up for our newsletter!").check()
        page.get_by_role("checkbox", name="Receive special offers from").check()

        # Address Information
        page.locator("#first_name").fill("Tejasvi")
        page.locator("#last_name").fill("Pratap")
        page.locator("#company").fill("XYZ Company")
        page.locator("#address1").fill("123 XYZ Street")
        page.locator("#address2").fill("Near XYZ Landmark")
        page.locator("#state").fill("Delhi")
        page.locator("#city").fill("New Delhi")
        page.locator("#zipcode").fill("110001")
        page.locator("#mobile_number").fill("9876543210")

        # Step 4: Create Account button click karo
        page.get_by_role("button", name="Create Account").click()

        # Confirmation ke liye thoda ruk jao (dekhne ke liye)
        page.wait_for_timeout(3000)

        browser.close()

test_complete_signup()
