- murder that occurred sometime on Jan.15, 2018 and that it took place in SQL City.

- Schema Diagram
  - interview (person_id, transcript)
  - get_fit_now_check_in (membership_id, check_in_date, check_in_time, check_out_time)
  - get_fit_now_member (id, person_id. name, membership_start_date, membership_status)
  - facebook_event_checkin (person_id, event_id, event_name, date)
  - crime_scene_report (date, type, description, city)
  - person (id, name, license_id, address_number, address_street_name, ssn)
  - solution (user, value)
  - income (ssn, annual_income)
  - drivers_license (id, age, height, eye_color, hair_color, gender, plate_number, car_make, car_model)

Step 1:
  ```
  SELECT *
  FROM get_fit_now_check_in
  where check_in_date = '20180115'
  ```
Output:
|membership_id	|check_in_date|	check_in_time	|check_out_time|
|---|---|---|---|
|D2KY6	|20180115|	746	|836|
|344VM|	20180115|	1087|	1195|
|3BRSC|	20180115|	354|	825|
|HM6U8|	20180115|	525|	800|

___
Step 2:
```
	SELECT *
 	FROM crime_scene_report
 	where date = '20180115' and city = 'SQL City'
```
Output:
|date	|type|	description|	city|
|---|---|---|---|
|20180115|	assault	|Hamilton: Lee, do you yield? Burr: You shot him in the side! Yes he yields!|	SQL City
|20180115|	assault	|Report Not Found	|SQL City
|20180115|	murder|	Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives somewhere on "Franklin Ave".	|SQL City
___

Step 3:
```
select * 
from person 
where name LIKE 'Annabel %'
```

Output:


|id	|name	|license_id	|address_number|	address_street_name|	ssn|
|---|----|---|---|---|---|
|16371	|Annabel Miller|	|490173	|103|	Franklin Ave	318771143

___

Step 4:
```
select * 
from person 
where address_street_name = 'Northwestern Dr' and address_number = (SELECT MAX(address_number) FROM person);

```
Output:
|id	|name	|license_id|	address_number|	address_street_name	|ssn|
|---|----|---|---|---|---|
|14887	|Morty Schapiro	|118009	|4919|	Northwestern Dr|	111564949

___

Step 5:
```
select * 
from get_fit_now_member
where name = 'Annabel Miller'

```

Output:
|id|	person_id|	name|	membership_start_date|	membership_status
|---|----|---|---|---|
|90081|	16371|	Annabel Miller|	20160208|	gold

___

Step 6:
```
select * 
from interview
where person_id = '16371'
```

Output:
|person_id	|transcript
|---|---
|16371	|I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th.
