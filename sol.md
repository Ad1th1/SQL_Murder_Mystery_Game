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
```
membership_id	
D2KY6	
344VM
3BRSC	
HM6U8	
```
___
Step 2:
```
	SELECT *
 	FROM crime_scene_report
 	where date = '20180115' and city = 'SQL City'
```
Output:
```
20180115	murder	
Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives
somewhere on "Franklin Ave".	
```
___
