    def enter_account_information(self, password, first_name, last_name,
                                  address, state, city, zipcode, mobile):

        self.page.locator("#id_gender1").check()

        self.page.locator("#password").fill(password)

        self.page.locator("#days").select_option("1")
        self.page.locator("#months").select_option("1")
        self.page.locator("#years").select_option("2000")

        self.page.locator("#newsletter").check()
        self.page.locator("#optin").check()

        self.page.locator("#first_name").fill(first_name)
        self.page.locator("#last_name").fill(last_name)

        self.page.locator("#address1").fill(address)

        self.page.locator("#country").select_option(label="India")

        self.page.locator("#state").fill(state)
        self.page.locator("#city").fill(city)
        self.page.locator("#zipcode").fill(zipcode)
        self.page.locator("#mobile_number").fill(mobile)

        self.page.get_by_role(
            "button",
            name="Create Account"
        ).click()
