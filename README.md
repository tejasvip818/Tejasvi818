from playwright.sync_api import sync_playwright

def test_open_login_page():
    with sync_playwright() as p:
        browser = p.chromium.launch(headless=False)
        page = browser.new_page()
        page.goto("https://automationexercise.com")
        
        # Ye wahi locator hai jo tumhe dikha
        page.get_by_role("link", name="Signup / Login").click()
        
        page.wait_for_timeout(3000)  # 3 second dekhne ke liye
        browser.close()

test_open_login_page()
