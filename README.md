from playwright.sync_api import Page


class SignupPage:

    def __init__(self, page: Page):
        self.page = page

        self.signup_login = page.get_by_text("Signup / Login")
        self.name = page.locator('input[data-qa="signup-name"]')
        self.email = page.locator('input[data-qa="signup-email"]')
        self.signup_button = page.get_by_role("button", name="Signup")

    def open_signup(self):
        self.signup_login.click()

    def enter_signup_details(self, name, email):
        self.name.fill(name)
        self.email.fill(email)
        self.signup_button.click()
