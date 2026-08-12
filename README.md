from pages.signup_page import SignupPage
from testdata.user_data import USERNAME, EMAIL


def test_register_user(page):

    page.goto("https://www.automationexercise.com/")

    signup_page = SignupPage(page)

    signup_page.open_signup()

    signup_page.enter_signup_details(
        USERNAME,
        EMAIL
    )
