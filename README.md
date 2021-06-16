# selenium_python
임시 repository


~~~py
from typing import KeysView
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC


# =============================================
# ====== < 통합관제 Web 사이트 접속하기 > =====
"""
_url1 = "https://kic-rs.lgerobot.com/rome"
drv1 = webdriver.Chrome("C:\chromedriver.exe")
drv1.get(_url1)

# id field가 보여질 때까지 Wait 
drv1.implicitly_wait(time_to_wait=5)
# =============================================
"""

# =============================================
# =========== < Yopmail 접속하기 > ============
_url2 = "https://yopmail.com/en/"
drv2 = webdriver.Chrome("C:\chromedriver.exe")
drv2.get(_url2)

# login field가 보여질 때까지 Wait 

drv2.find_element(By.ID, 'login').send_keys('rsdp_op_app@yopmail.com'+Keys.ENTER)
drv2.implicitly_wait(time_to_wait=5)
#drv2.find_element_by_partial_link_text('LOGIN OTP PASSWORD').click()
#print("//*[@id="'e_ZwRjAwR0ZQL0ZwZ2ZQNjZGp4ZmR5BN=='"]/button/div[(text()='LOGIN OTP PASSWORD')]")

#iframes = drv2.find_elements_by_css_selector('iframe')
#for iframe in iframes:
#    print(iframe.get_attribute('name'))
drv2.switch_to.frame('ifinbox')
drv2.find_element(By.XPATH, '''//*[@id="e_ZwRjAwR0ZQL0ZwZ2ZQNjZGp4ZmR5BN=="]/button/div[contains(text(),'LOGIN OTP PASSWORD')]''').click()

drv2.switch_to.frame('ifnoinb')
drv2.switch_to.frame('ifmail')
otp_text = drv2.find_element(By.XPATH, '''//*[@id="mail"]/div/table/tbody/tr/td/table[1]/tbody/tr/td/table/tbody/tr[2]/td/table/tbody/tr/td/table/tbody/tr[2]/td''').text()
print('OTP : ' + otp_text)


~~~
