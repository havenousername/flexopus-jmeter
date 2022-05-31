# Flexopus Jmeter 

## Simple Jmeter Performance tester for Login & Booking Proccess

### Environment Configuration 

1. Download JMeter Apllication and have JVM installed on your PC 
   Links: 
   - [JMeter Official Website](https://jmeter.apache.org/) (For macos `brew` package manager can be used)
   - [Java Documentation](https://www.java.com/en/download/manual.jsp)
2. Open `LoginAndBooking.jmx` though JMeter
3. Open `jmeter.properties` inside `bin` directory of installed version of jmeter. E.g. for mac brew installation the path is `/usr/local/opt/jmeter`. Uncomment `CookieManager.save.cookies` property, and change its value to `true` (This is needed for correct cookie-manager bahaivior). 
4. Configure ThreadGroups and Run the Tests 


### Test Plan Explanation

1. Http Header Manager - helps to set the headers for the requests
2. Http Cookie Manager - automatically takes and puts the cookies values from the response to the request
3. User Defined Variables - config with variables used for testing (usually some parts of url)
4. HTTP(S) script recorder - **disabled**, special way of recording the requests made up in the browser and transoforming them into `HTTP Request Sample` samplers
5. Thread Group - **disabled**, place of samplers made up due to the HTTP(S) recorder activity 
6. BookingProcess - Thread Group of the main workflow testing, you can configure `Thread Properties` for different types of testings
   Has inside `GraphResults` Listener for viewing the graph representation of testing activity.
8. Logout From Booking - `teadDown` thread group. Log's out the user from the testing application
9. Other components - Listeners for debugging, Timers - simulating life usecases, Extractors (inside samplers) - used for taking info for next request, etc.


### Testings

1. 100 concurrent users + 1 sec. ramp up
<img width="1645" alt="Screenshot 2022-05-30 at 23 37 44" src="https://user-images.githubusercontent.com/40630843/171074608-ef595333-2306-46fb-a3ae-856c7ca37beb.png">
2. 40 concurrent users + 40 sec. ramp up
<img width="1356" alt="Screenshot 2022-05-30 at 23 48 30" src="https://user-images.githubusercontent.com/40630843/171074679-41af6759-ed4c-47f1-a186-4a66ac2a23bb.png">
3. 40 concurrent users + 1 sec. ramp up + 10 loops
<img width="1335" alt="Screenshot 2022-05-30 at 23 56 45" src="https://user-images.githubusercontent.com/40630843/171074747-a1f91082-008d-4673-a1c8-af2624d6b528.png">
4. 40 concurrent users + 40 sec. ramp up + 10 mins. duration
<img width="1672" alt="Screenshot 2022-05-31 at 1 32 36" src="https://user-images.githubusercontent.com/40630843/171074788-6ab8a2dd-d41b-48c0-858e-c82d96e8e7aa.png">
