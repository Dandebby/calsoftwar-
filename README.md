# calsoftwar-

import time
from selenium import webdriver
from (link unavailable) import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Set up the webdriver
driver = webdriver.Chrome()  # Replace with your preferred browser

# Launch LDD
driver.get("(link unavailable)")

# Wait for the UI to load
WebDriverWait(driver, 10).until(EC.visibility_of_element_located((By.XPATH, "//button[@data-test='toolbar-new-project']")))

# Test the "New Project" button
new_project_button = driver.find_element(By.XPATH, "//button[@data-test='toolbar-new-project']")
new_project_button.click()

# Test the "Open" dialog
open_dialog = driver.find_element(By.XPATH, "//div[@data-test='file-open-dialog']")
open_dialog_title = open_dialog.find_element(By.TAG_NAME, "h1")
assert open_dialog_title.text == "Open"

# Test the "Cancel" button
cancel_button = open_dialog.find_element(By.XPATH, "//button[@data-test='file-open-dialog-cancel']")
cancel_button.click()

# Test the "Grid" toggle
grid_toggle = driver.find_element(By.XPATH, "//button[@data-test='grid-toggle']")
grid_toggle.click()

# Test the "Grid" visibility
grid_container = driver.find_element(By.XPATH, "//div[@data-test='grid-container']")
assert grid_container.is_displayed()

# Clean up
driver.quit()
