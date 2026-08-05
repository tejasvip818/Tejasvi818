import re
from playwright.sync_api import Page, expect

def test_verify_pwlocators(page: Page):

    page.goto("https://demo.nopcommerce.com/")
    page.wait_for_timeout(5000)

    # 1) get_by_alt_text()
    logo = page.get_by_alt_text("nopCommerce demo store")
    expect(logo).to_be_visible()

    # 2) get_by_text()
    expect(page.get_by_text("Welcome to our store")).to_be_visible()
    expect(page.get_by_text("Welcome to")).to_be_visible()
    expect(page.get_by_text(re.compile(".*Welcome.*"))).to_be_visible()

    # 3) get_by_role()
    page.goto("https://demo.nopcommerce.com/register?returnUrl=%2F")
    expect(
        page.get_by_role("heading", name="Register")
    ).to_be_visible()
