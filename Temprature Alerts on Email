//Email and SMS configuration

SID = ' ' 
AUTH_TOKEN = ' ' 
FROM_NUMBER = ' '
TO_NUMBER = ' '
MAILGUN_API_KEY = ' ' 
SANDBOX_URL= ' ' 
SENDER_EMAIL = 'test@' + SANDBOX_URL  # No need to modify this. The sandbox URL$
RECIPIENT_EMAIL = ' '
API_KEY = 'Enter your Own'
DEVICE_ID = 'BOLTXXXX'

//Temprature Alerts via Email

import email_conf
from boltiot import Email, Bolt
import json, time

minimum_limit = 300 #the minimum threshold of light value 
maximum_limit = 600 #the maximum threshold of light value 


mybolt = Bolt(email_conf.API_KEY, email_conf.DEVICE_ID)
mailer = Email(email_conf.MAILGUN_API_KEY, email_conf.SANDBOX_URL, email_conf.SENDER_EMAIL, email_co$


while True: 
    print ("Reading sensor value")
    response = mybolt.analogRead('A0') 
    data = json.loads(response) 
    print ("Sensor value is: " + str(data['value']))
    try: 
        sensor_value = int(data['value'])*(100/1024) 
        if sensor_value > maximum_limit or sensor_value < minimum_limit:
            print("Making request to Mailgun to send an email")
            response = mailer.send_email("Alert", "The Current temperature sensor value is " +str(se$
            response_text = json.loads(response.text)
            print("Response received from Mailgun is: " + str(response_text['message']))
    except Exception as e: 
        print ("Error occured: Below are the details")
        print (e)
    time.sleep(10)
    
    
    //Temprature Alerts via SMS
    
    import conf
from boltiot import Sms, Bolt
import json, time

minimum_limit = 300
maximum_limit = 600  


mybolt = Bolt(conf.API_KEY, conf.DEVICE_ID)
sms = Sms(conf.SID, conf.AUTH_TOKEN, conf.TO_NUMBER, conf.FROM_NUMBER)


while True: 
    print ("Reading sensor value")
    response = mybolt.analogRead('A0') 
    data = json.loads(response) 
    print("Sensor value is: " + str(data['value']))
    try: 
        sensor_value = int(data['value'])*(100/1024) 
        if sensor_value > maximum_limit or sensor_value < minimum_limit:
            print("Making request to Twilio to send a SMS")
            response = sms.send_sms("The Current temperature sensor value is " +str(sensor_value)+" $
            print("Response received from Twilio is: " + str(response))
            print("Status of SMS at Twilio is :" + str(response.status))
    except Exception as e: 
        print ("Error occured: Below are the details")
        print (e)
    time.sleep(10)
