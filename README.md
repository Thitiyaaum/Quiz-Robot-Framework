*** Settings *** 
Library    SeleniumLibrary

Suite Setup    Open Browser    ${URL}    ${BROWSER}
Suite Teardown    Close Browser

*** Variables ***
${URL}        http://automationexercise.com
${BROWSER}    Chrome
${EMAIL}      fknksdni@gmail.com
${PASSWORD}   123456789

*** Keywords ***
CLICK SIGNUP LOGIN
    Click Element    xpath=//a[contains(text(), 'Signup / Login')]
    Wait Until Page Contains    Login to your account

INPUT EMAIL
    [Arguments]    ${EMAIL}
    Input Text    name=email    ${EMAIL}

INPUT PASSWORD
    [Arguments]    ${PASSWORD}
    Input Text    name=password    ${PASSWORD}

CLICK LOGIN BUTTON
    Click Button    xpath=//button[contains(text(), 'Login')]

VERIFY ERROR MESSAGE
    Wait Until Page Contains    Your email or password is incorrect!

*** Test Cases ***
Login With Incorrect Email And Password
    CLICK SIGNUP LOGIN
    INPUT EMAIL    ${EMAIL}
    INPUT PASSWORD    ${PASSWORD}
    CLICK LOGIN BUTTON
    VERIFY ERROR MESSAGE
