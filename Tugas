import unittest
import time
from selenium import webdriver
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support.wait import WebDriverWait

class Login(unittest.TestCase): # test scenario

    def setUp(self):
        self.browser = webdriver.Chrome(ChromeDriverManager().install())

    def test_failed_login(self): #test cases 1
        driver = self.browser
        driver.get("https://www.saucedemo.com/")
        driver.find_element(By.ID, "user-name").send_keys("haitest")
        time.sleep(1)
        driver.find_element(By.NAME, "login-button").click()
        time.sleep(3)
        error_message = driver.find_element(By.CSS_SELECTOR, "[data-test='error']").text
        self.assertIn("Epic sadface: Password is required", error_message)

    def test_a_success_login(self): #Test case 2 Success login
# steps
        driver = self.browser #buka web browser
        driver.get("https://www.saucedemo.com/") # buka situs
        time.sleep(3)
        driver.find_element(By.ID,"user-name").send_keys("standard_user") # isi email
        time.sleep(1)
        driver.find_element(By.ID, "password").send_keys("secret_sauce") # isi password
        time.sleep(1)
        driver.find_element(By.CSS_SELECTOR, '[data-test="login-button"]').click()
        time.sleep(1)
# validasi
        response_data = driver.find_element(By.CLASS_NAME,"title").text
        self.assertIn('Products', response_data)

    def test_checkout_item(self): #test cases 3
        driver = self.browser
        driver.get("https://www.saucedemo.com/")
        driver.find_element(By.ID, "user-name").send_keys("standard_user")
        driver.find_element(By.CSS_SELECTOR, "[data-test='password']").send_keys("secret_sauce")
        driver.find_element(By.NAME, "login-button").click()
        driver.find_element(By.CSS_SELECTOR, '[data-test="add-to-cart-sauce-labs-backpack"]').click()
        time.sleep(2)
        driver.find_element(By.CLASS_NAME, "shopping_cart_link").click() #klik shopping cart
        time.sleep(2)
        driver.find_element(By.CSS_SELECTOR, '[data-test="checkout"]').click() #klik chechout
        time.sleep(1)
        driver.find_element(By.ID,"first-name").send_keys("Ikhlas") #isi nama depan
        driver.find_element(By.ID, "last-name").send_keys("Aminuddin") #isi nama belakang
        driver.find_element(By.ID, "postal-code").send_keys("12345") #kode pos
        time.sleep(2)
        driver.find_element(By.CSS_SELECTOR, '[data-test="continue"]').click() #klik continue
        time.sleep(2)
        driver.find_element(By.CSS_SELECTOR, '[data-test="finish"]').click() #klik finish
        time.sleep(2)
        response_message = driver.find_element(By.CLASS_NAME, "complete-header").text
        self.assertIn("Thank you for your order!", response_message)
        
if __name__ == '__main__':
    unittest.main()
