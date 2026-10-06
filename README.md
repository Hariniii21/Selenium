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

```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

driver = webdriver.Chrome()
wait = WebDriverWait(driver, 20)

# 1. Open Amazon
driver.get("https://www.amazon.in/")
driver.maximize_window()

print("1. Amazon opened")

# 2. Search product
search_box = wait.until(
    EC.element_to_be_clickable((By.ID, "twotabsearchtextbox"))
)

search_box.send_keys("Womens Yellow Kurti")
search_box.send_keys(Keys.ENTER)

print("2. Product searched")

time.sleep(5)

# 3. Find product links directly
product_links = driver.find_elements(
    By.XPATH,
    "//a[contains(@href, '/dp/') or contains(@href, '/gp/aw/d/')]"
)

print("3. Product links found:", len(product_links))

if len(product_links) == 0:
    print("No product link found.")
    input("Press Enter to close...")
    driver.quit()
    exit()

# 4. Get first product link
product = product_links[0]

product_name = product.text
product_link = product.get_attribute("href")

print("4. Product found")
print("Product name:", product_name)
print("Product link:", product_link)

# 5. Open product
driver.get(product_link)

print("5. Product page opened")

time.sleep(5)

# 6. Find Add to Cart
add_to_cart = wait.until(
    EC.presence_of_element_located(
        (By.ID, "add-to-cart-button")
    )
)

print("6. Add to Cart button found")

# Scroll to button
driver.execute_script(
    "arguments[0].scrollIntoView({block: 'center'});",
    add_to_cart
)

time.sleep(1)

# Click Add to Cart
driver.execute_script(
    "arguments[0].click();",
    add_to_cart
)

print("7. Product added to cart!")

time.sleep(4)

# 8. Open cart
cart = wait.until(
    EC.element_to_be_clickable((By.ID, "nav-cart"))
)

cart.click()

print("8. Cart opened")

time.sleep(3)

print("9. Product in cart:")
print(product_name)

input("Press Enter to close browser...")

driver.quit()
```

# Output

<img width="1393" height="751" alt="image" src="https://github.com/user-attachments/assets/5e6ff92c-55a5-4503-8889-6175f5650f43" />

<img width="1405" height="752" alt="image" src="https://github.com/user-attachments/assets/6058d9ac-d697-41ea-904b-7836065bfec7" />
