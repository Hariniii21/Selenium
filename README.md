# Selenium
```
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()

try:
    # 1. Open the demo site URL
    driver.get("https://vinothqaacademy.com/demo-site/")
    driver.maximize_window()

    wait = WebDriverWait(driver, 10)

    # 2. First Name
    first_name = wait.until(EC.presence_of_element_located((By.XPATH, "//input[contains(@id, 'vfb-5') or @name='vfb-5']")))
    first_name.send_keys("HARINI")

    # 3. Last Name
    last_name = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-7') or @name='vfb-7']")
    last_name.send_keys("S")

    # 4. Gender (Radio Button - Female Selection)
    female_radio_label = driver.find_element(By.XPATH, "//label[contains(text(),'Female') or @for='vfb-31-2'] | //input[@value='Female']")
    driver.execute_script("arguments[0].click();", female_radio_label)

    # 5. Course Interested (Checkbox - Selenium WebDriver)
    selenium_checkbox = driver.find_element(By.XPATH, "//input[@type='checkbox' and (contains(@value, 'Selenium') or @id='vfb-20-0')]")
    if not selenium_checkbox.is_selected():
        selenium_checkbox.click()

    # 6. Address Fields
    # Address Line 1
    address_line1 = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-13-address') or contains(@name, 'vfb-13[address]')]")
    address_line1.send_keys("I BLOCK")

    # Street Address Line 2 (Apt, Suite, Bldg)
    address_line2 = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-13-address-2') or contains(@name, 'vfb-13[address-2]')]")
    address_line2.send_keys("5th cross street,Thirumazisai")

    # City
    city = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-13-city') or contains(@name, 'vfb-13[city]')]")
    city.send_keys("Chennai")

    # State / Province / Region
    state = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-13-state') or contains(@name, 'vfb-13[state]')]")
    state.send_keys("Tamil Nadu")

    # Postal / Zip Code
    postal = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-13-zip') or contains(@name, 'vfb-13[zip]')]")
    postal.send_keys("600124")

    # 7. Email Input
    email_field = driver.find_element(By.XPATH, "//input[contains(@id, 'vfb-14') or @type='email']")
    email_field.send_keys("inirah.268@gmail.com")

    # Output filled values to console in English
    print("\n--- Registration Form Details Filled ---")
    print("First Name :", first_name.get_attribute("value"))
    print("Last Name  :", last_name.get_attribute("value"))
    print("Gender     : Female")
    print("Email      :", email_field.get_attribute("value"))
    print("----------------------------------------\n")

    time.sleep(20)

except Exception as e:
    print("An error occurred:", e)

finally:
    driver.quit()
```
# Output
<img width="1887" height="966" alt="image" src="https://github.com/user-attachments/assets/798ae977-242a-453a-a302-d6f3ed9a5672" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9a7fb5ed-d41f-4a26-8ac5-61f330a1ddd7" />
