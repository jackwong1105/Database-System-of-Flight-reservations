The reservation department of an airline makes use of the following paper-based form
to record confirmed passenger reservations. The airline has issues that this form
cannot handle special requests of passengers. Examples of special requests can be
child meal, vegetarian meal, use of wheel chairs, over-sized luggages, etc. A database
is to be designed to handle the reservations as well as special requests.

Legend:
 A flight number represents a trip from the departing city to the destinating city
without stopping over any other cities.
 For regular flights on daily basis, the same flight number represents the same
trip at the same time interval on every day.
 For flights of the same trip but different time intervals, different flight
numbers are assigned.

Additional information :
 There is no additional charge per special request.
 A passenger may have many special requests in a flight.
 It is not required to save current special requests of a passenger for use in future
flights.
 Passengers in a group (e.g. a family having 4 members) are handled individually.

Business needs
⚫ Record confirmed passenger reservation everyday
⚫ Check the VIP status of different passenger to provide different special
privileges, such as lounge, priority boarding and welcome drink
⚫ Check the Food Allergies status of different passenger to prevent providing
allergic meal to passenger and inform flight kitchens to prepare appropriate
food
⚫ List the Special Assistance status of different passenger to provide advanced
action, such as prepare one more seats for assistance dog, pay attention to
passenger who have medical device
⚫ List the Special Requests status of different passenger on their flight to provide
advanced action, such as provide child meal and vegetarian meal to passenger,
prepare one more seats for wheel chair, provide advanced action to over-sized
luggages and overweight luggages
⚫ Provide the status summary including which flight is the most popular during a
week

Table FLIGHT
Basic information of each flight,
Flight_No is primary key and provide the number of each flight
Flight_FromCity and Flight_DepartureTime provide departure time and city
Flight_ToCity and Flight_ArrivalTime provide arrival time and city
Flight_TotalTime provide total time of each flight
Flight_TotalSeats provide total seats of each flight

Table PASSENGER
Basic information of each passenger,
Passenger_No is primary key
Passenger_FirstName and Passenger_LastName provide the first name and last name
of each passenger
Passenger_Gender provide the gender of each passenger
VIP_Code is a foreign key to link with table VIP to provide the level of VIP and
special privileges
Passenger_PassportNumber provide the passport number of each passenger
Passenger_Nationality provide the nationality of each passenger
Passenger_Birthday provide the birthday of each passenger
Passenger_PhoneNumber provide the phone number of each passenger
Passenger_Email provide the email of each passenger
Passenger_AssistanceDog include a value either YES or No to determines the special
need of assistance dog
FoodAllergies_Code is a foreign key to link with table FOODALLERGIES and
provide information of food allergies on each passenger
Passenger_MedicalDevice include a value either YES or No to provide the special
need to passenger who have medical device

Table CLASS
Basic information of each cabin,
Class_Code is primary key and provide the alphabet represent different cabin
Class_Cabin provide different cabin

Table VIP
Basic information of each VIP level,
VIP_Code is primary key and represent different VIP level
VIP_Lounge include a value either YES or No to determines the permission of entry
the lounge on the airport
VIP_PriorityBoarding include a value either YES or No to determines the order of
priority boarding between VIP and non-VIP
VIP_WelcomeDrink include a value either YES or No to provide the welcome drink
to the VIP of ‘Gold’ level

Table FOODALLERGIES
Basic information of different food allergies,
FoodAllergies_Code is primary key and provide the special code to represent
different allergic food
FoodAllergies_Food include different allergic food

Table INVOICE
Basic information of different invoice of different passenger,
Invoice_No is primary key and represent different number of invoice
Invoice_Date is the date of the flight
Flight_No is a foreign key and link to the primary key “Flight_No” of table FLIGHT
and state the flight number which passenger will take
Passenger_No is a foreign key and link to the primary key “Passenger_No” of table
PASSENGER in order to state the information of each passenger
Class_Code is a foreign key and link to the primary key “Class_Code” of table
CLASS in order to state the class
Invoice_SeatRow provide the row of seat of each passenger on the flight
Invoice_SeatNo provide the no of seat of each passenger on the flight
Invoice_ChildMeal include a value either YES or No to determines the child meal of
each passenger
Invoice_VegetarianMeal include a value either YES or No to determines the
vegetarian meal of each passenger
Invoice_WheelChairs include a value either YES or No to determines the special need
of wheel chairs
Invoice_OverSizedLuggages include a value either YES or No to show the over sized
luggages on each passenger
Invoice_OverWeightLuggages include a value either YES or No to determines the
overweight luggages on each passenger

Assumptions and Limitations
⚫ All passengers have their flight during a period (2022/04/05 to 2022/04/11)
⚫ If first time user booked a flight ticket on our flight reservations, it will become
the basic VIP level – bronze level and record it on the database
⚫ How Passenger use our Flight Reservations
◼ Passenger will enter their information, such as name, gender, passport
number, their VIP code and select their special needs (Assistance Dog,
Food Allergies, Medical Device)
◼ Then Passenger will choose their flight, Cabin, Seat Row and number, also
select their special request (Child Meal, Vegetarian Meal, Use of wheel
chairs, Over-sized Luggages, Overweight Luggages)
◼ Above steps must not contain blank information and must not skip each
step
⚫ If a passenger didn’t choose their flight, database will only save his/her
information and will not have his/her own invoice
⚫ If a flight was cancelled due to different cause and deleted on table FLIGHT,
flight number on table INVOICE will be error and be confusing as they are no
corresponding foreign key on table FLIGHT
⚫ If a passenger have food allergies that do not include in table
“FOODALLERGIES”, it will not record it as the flight reservations only allow
passenger choose the allergy food and they can’t type it on the flight
reservations. It neglect the real situation of different people.

Conclusion
This design basically supports the stated requirements. In future, this design
should be enhanced to cater for:
⚫ Passenger not entering some unimportant information
⚫ Summary on passenger who have not use our flight reservation system in
a year
⚫ Summary on passenger who always use our flight reservation system in a
year
⚫ Summary on passenger who always requests different special requests in
a year
⚫ Summary on gold VIP level passenger and which flight is the most taken
among gold VIP level passenger
⚫ Summary on how passenger choose the cabin under different situation,
such as total flight time, destinations
⚫ Not enforcing passenger become a bronze level VIP after they use our
flight reservation system, system can add a Non-VIP on VIP code
⚫ System also can add a visitors function. Under the visitors function,
visitors can browse our system to check the time or destination of flight
without entering personal information and becoming a VIP
⚫ Allow passenger enter their allergy food which is not include in our list to
protect the health of passenger and flight company
⚫ Allow passenger enter their special requests in a comment box which is
not include in the part of special requests or add more new special
requests, such as require a window seats or aisle seats, require to seat
with his/her family member, passenger with wheelchair or with children
require to priority boarding, require an emergency exit row seat to have
more space, require a seat which is far away from toilet or close to the
kitchen
