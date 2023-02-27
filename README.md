These units sound good in theory but suffer from serious design flaws. A "smart" cat feeder is supposed to be smart, right?

After massive frustation trying to use some other guys petkit home assistant integration that DOES NOT WORK (why hasnt anyone cracked this egg wide open yet?)  I brute force fixed this frigging pet feeder to finally work propertly.

I bought this one:
https://www.amazon.com/gp/product/B09158J9PF/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1

- it always fails to correctly sense when its out of food
- often disonnects from the tuya servers

What to do? Add a D1 mini loaded with local ESPHome code and finally make it work. The food sensor tries to count the number of pellets dropping into the bowl.  It fails miserably.  my solution actually senses when THERE IS NO FOOD in the bin!  what a totally novel concept...And all you need to add is a D1 mini, drill a couple of holes and reroute a couple wires.

![C8CFE5C7-FA86-4300-BD76-43160CD2ABBC_1_105_c](https://user-images.githubusercontent.com/52110065/213883379-4ff87d65-74a6-40ab-84d6-570e7a944991.jpeg)
![697E323B-5C39-47F1-928E-9A1A5988D3E6_1_105_c](https://user-images.githubusercontent.com/52110065/213883384-26c42ae2-a074-4336-87b1-b884584001e4.jpeg)
![BDDA6EA5-35E7-4F2B-911A-461EAD554BFE_1_105_c](https://user-images.githubusercontent.com/52110065/213883386-9b276ed5-ddde-4d96-a99f-f87fa5d53c43.jpeg)
![4C9666E9-9F02-466C-ADBC-7C2C841C21D3_1_105_c](https://user-images.githubusercontent.com/52110065/213883391-f1463958-ebc9-407f-9df8-4b3ef440cb81.jpeg)


Remove and Extend the wires on the existing send/receive food sensors and then mount them on each side of the food bin by drilling (2) 1/4" holes opposite each other about 1" above the bottom of the food bin and hot glue them in place.  now when the food gets low, they can acually sense that there is no food between them RELIABLY, every single time!

![47EDB970-2489-478A-9DF1-23DF3CC5832D](https://user-images.githubusercontent.com/52110065/221619516-9b7fd5d9-8d7e-4225-bef1-678daac77ab0.jpeg)
![86DA7FFB-E39B-4360-A6FE-DFF0467371DC](https://user-images.githubusercontent.com/52110065/221619547-1854e50f-ab68-45b0-a795-64409591390a.jpeg)


To trigger this sensor, At first I tried to sense when the buzzer sounded during feeding time using a pwm sensor routine, but that proved impossible... so now I just sense when the motor turns using a zener diode. Simple, reliable and consistent.

I put a 3.3v Zener diode and 1k resistor (this converts the higher motor voltage to 3.3v) on the motor to give me a "HIGH" signal when the motor runs during feeding. This triggers the routine to sense if there is food in the bin. 

Now, every time food is dispensed, it checks if food is in the food bin. Why the idiots that designed this cat feeder didnt do this is beyond me.

If I was more patient, I would have added a wire to control the motor on/off.  then I could completely get rid of the invasive Tuya cloud.  But, I was in a hurry the day I did this and the petkit app makes it easy to program the food delivery, which works well.
