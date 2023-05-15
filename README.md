# Develop-automation-
#Develop automation for User Management Tool by adding a user
import time
from lib2to3.pgen2 import driver

import requests as requests
import select
from selenium import webdriver
from selenium.webdriver.chrome import service
from selenium.webdriver.common.by import By
from urllib3.util import url
from selenium.webdriver.support.select import Select


# *** Develop automation for User Management Tool by adding a user ***

class OrangeHRM:
    url = "https://opensource-demo.orangehrmlive.com/"
    driver = webdriver.Chrome()
    driver.get(url)
    driver.maximize_window()
    time.sleep(2)

    # Created Method to login
    def test_login(self):
        username = "Admin"
        password = "admin123"
        self.driver.get(self.url)
        time.sleep(3)
        # Need to relax should provide time frame
        username_xpath = '//input[@name="username"]'
        password_xpath = '//input[@name="password"]'
        submit_button_xpath = '//button[@type="submit"]'
        time.sleep(3)
        # Created Username1 Password1(Variables) and assigned to XPath's
        username_1 = self.driver.find_element(by=By.XPATH, value=username_xpath)
        password_2 = self.driver.find_element(by=By.XPATH, value=password_xpath)
        submit_button = self.driver.find_element(by=By.XPATH, value=submit_button_xpath)

        username_1.send_keys(username)
        password_2.send_keys(password)
        submit_button.click()
        time.sleep(3)
        print("Successfully logged_in")

    # clicked on Create New Employee Button and providing the Employee Details

    def create_employee(self):
        create_employee = '//div[@class="orangehrm-header-container"]/button[@type="button"]'
        create_employee_1 = self.driver.find_element(by=By.XPATH, value=create_employee)
        create_employee_1.click()
        time.sleep(3)
        print("EmployeeButton Clicked")

    def employee_details(self):
        employee_firstname = 'input[name="firstName"]'
        employee_firstname_2 = self.driver.find_element(by=By.CSS_SELECTOR, value=employee_firstname)
        employee_firstname_2.send_keys("Nirmal")
        time.sleep(3)
        print("First_Name Added")

        employee_middlename = '//input[@name="middleName"]'
        employee_middlename_3 = self.driver.find_element(by=By.XPATH, value=employee_middlename)
        employee_middlename_3.send_keys("Narayan")
        time.sleep(3)
        print("Middle_Name Added")

        employee_lastname = '//input[@name="lastName"]'
        employee_lastname_4 = self.driver.find_element(by=By.XPATH, value=employee_lastname)
        employee_lastname_4.send_keys("Motilal")
        time.sleep(3)
        print("Last_Name Added")

        # Click on Create Login Details for Adding Additional Details.
        Login_detailsbutton = '//span[@class="oxd-switch-input oxd-switch-input--active --label-right"]'
        Login_detailsbutton_5 = self.driver.find_element(by=By.XPATH, value=Login_detailsbutton)
        Login_detailsbutton_5.click()
        time.sleep(3)
        print("Login Button Clicked Successfully")

        # Enter Username
        new_username = 'div.oxd-layout div.oxd-layout-container div.oxd-layout-context ' \
                       'div.orangehrm-background-container div.orangehrm-card-container form.oxd-form ' \
                       'div.orangehrm-employee-container div.orangehrm-employee-form div.oxd-form-row:nth-child(4) ' \
                       'div.oxd-grid-2.orangehrm-full-width-grid div.oxd-grid-item.oxd-grid-item--gutters:nth-child(' \
                       '1) div.oxd-input-group.oxd-input-field-bottom-space div:nth-child(2) > ' \
                       'input.oxd-input.oxd-input--active '
        new_username_6 = self.driver.find_element(by=By.CSS_SELECTOR, value=new_username)
        new_username_6.send_keys("Nirmal005")
        time.sleep(3)
        # Enter Password
        new_password = 'div.oxd-layout div.oxd-layout-container div.oxd-layout-context ' \
                       'div.orangehrm-background-container div.orangehrm-card-container form.oxd-form ' \
                       'div.orangehrm-employee-container div.orangehrm-employee-form ' \
                       'div.oxd-form-row.user-password-row:nth-child(5) div.oxd-grid-2.orangehrm-full-width-grid ' \
                       'div.oxd-grid-item.oxd-grid-item--gutters.user-password-cell:nth-child(1) ' \
                       'div.oxd-input-group.oxd-input-field-bottom-space div:nth-child(2) > ' \
                       'input.oxd-input.oxd-input--active '
        new_password_7 = self.driver.find_element(by=By.CSS_SELECTOR, value=new_password)
        new_password_7.send_keys("Nirmalmba555@")
        time.sleep(3)
        # Confirm Password
        confirm_password = 'div.oxd-layout div.oxd-layout-container div.oxd-layout-context ' \
                           'div.orangehrm-background-container div.orangehrm-card-container form.oxd-form ' \
                           'div.orangehrm-employee-container div.orangehrm-employee-form ' \
                           'div.oxd-form-row.user-password-row:nth-child(5) div.oxd-grid-2.orangehrm-full-width-grid ' \
                           'div.oxd-grid-item.oxd-grid-item--gutters:nth-child(2) ' \
                           'div.oxd-input-group.oxd-input-field-bottom-space div:nth-child(2) > ' \
                           'input.oxd-input.oxd-input--active '
        confirm_password_8 = self.driver.find_element(by=By.CSS_SELECTOR, value=confirm_password)
        confirm_password_8.send_keys("Nirmalmba555@")

        # Click on Submit button to save the data

        submit_button = '//button[@type="submit"]'
        submit_button_9 = self.driver.find_element(by=By.XPATH, value=submit_button)
        submit_button_9.click()
        print("Created New Employee Successfully")

        # Click on Admin Panel to verify the Employee name is added successfully

        lhs_admin_panel = '//*[@id="app"]/div[1]/div[1]/aside/nav/div[2]/ul/li[1]/a'
        lhs_admin_panel_10 = self.driver.find_element(by=By.XPATH, value=lhs_admin_panel)
        lhs_admin_panel_10.click()
        print("LHS ADMIN Panel clicked successfully")

    # *** Now once we created the Employee details we Need to Verify the username & Details ***
    def verify_details(self):
        verify_username = '/html/body/div/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[1]/div/div[1]/div/div[' \
                          '2]/input '
        verify_username_11 = self.driver.find_element(by=By.XPATH, value=verify_username)
        verify_username_11.send_keys("Nirmal005")
        time.sleep(3)

        dropdown_ess = '//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[1]/div/div[2]/div/div[' \
                       '2]/div/div[1]/div[2]/i '
        dropdown_ess_13 = self.driver.find_element(by=By.XPATH, value=dropdown_ess)
        dropdown_ess_13.click()
        time.sleep(3)
        dropdown_select = '/html/body/div/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[1]/div/div[2]/div/div[' \
                          '2]/div/div[2]/div[3] '
        dropdown_select_14 = self.driver.find_element(by=By.XPATH, value=dropdown_select)
        dropdown_select_14.click()
        time.sleep(3)
        print("Clicked Successfully")
        dropdown_employee = '//input[@placeholder="Type for hints..."]'
        dropdown_employee_15 = self.driver.find_element(by=By.XPATH, value=dropdown_employee)
        dropdown_employee_15.send_keys("Nirmal Narayan Motilal")
        # Select Enable Option

        enable_option = '//*[@id="app"]/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[1]/div/div[4]/div/div[' \
                        '2]/div/div/div[2]/i '
        enable_option_16 = self.driver.find_element(by=By.XPATH, value=enable_option)
        enable_option_16.click()

        enable_click = '/html/body/div/div[1]/div[2]/div[2]/div/div[1]/div[2]/form/div[1]/div/div[4]/div/div[' \
                       '2]/div/div[2]/div[2] '
        enable_click_17 = self.driver.find_element(by=By.XPATH, value=enable_click)
        enable_click_17.click()
        time.sleep(3)
        print("Enable option clicked successfully")

        search_button_value = '//button[@type="submit"]'
        search_button = self.driver.find_element(by=By.XPATH, value=search_button_value)
        search_button.click()
        print("Able to find the name Successfully")

        logout_dropdown = self.driver.find_element(by=By.CSS_SELECTOR, value=".oxd-userdropdown-name")
        logout_dropdown.click()
        logout_dropdown_button = '//a[@href="/web/index.php/auth/logout"]'
        logout_dropdown_button_18 = self.driver.find_element(by=By.XPATH, value=logout_dropdown_button)
        logout_dropdown_button_18.click()

    # Logged off from the page and re_login with new credentials.

    def re_login(self):
        username_new = "Nirmal005"
        password_new = "Nirmalmba555@"
        self.driver.get(self.url)
        time.sleep(3)
        # Need to relax should provide time frame
        username_xpath_1 = '//input[@name="username"]'
        password_xpath_2 = '//input[@name="password"]'
        submit_button_xpath = '//button[@type="submit"]'
        time.sleep(3)
        # Created Username1 Password1(Variables) and assigned to XPath's
        username_19 = self.driver.find_element(by=By.XPATH, value=username_xpath_1)
        password_20 = self.driver.find_element(by=By.XPATH, value=password_xpath_2)
        submit_button = self.driver.find_element(by=By.XPATH, value=submit_button_xpath)

        username_19.send_keys(username_new)
        time.sleep(3)
        password_20.send_keys(password_new)
        time.sleep(3)
        submit_button.click()
        time.sleep(3)
        print("Successfully logged_in")


O = OrangeHRM()
O.test_login()
O.create_employee()
O.employee_details()
O.verify_details()
O.re_login()
