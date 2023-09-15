show databases;
create database project_2;
use project_2;

select * from sql_project;

create table NYC_1(id int, name char(255), host_id int, host_name char(255), neighbourhood_group char(255),	
neighbourhood char(255), room_type char(255));

select * from nyc_1;

create table NYC_2(id int,	price int,	minimum_nights int,	number_of_reviews int, reviews_per_month float,	
calculated_host_listings_count int,	availability_365 int);

select * from nyc_2;


# 1. write query to show name from NYC_1

select name from nyc_1;

# 2. write query to show count of id in nyc_1

select count(id) from nyc_1;

# 3. write query to show count of id in nyc_2

select count(id) from nyc_2;

# 4. write query to show host id in nyc_1

select host_id from nyc_1;

# 5. write query to show all unique host id from nyc_1

select distinct host_id from nyc_1;

# 6. write query to show all unique neighbourhood_group from nyc_1

select distinct neighbourhood_group from nyc_1;

# 7. write query to show all unique neighbourhood from nyc_1

select distinct neighbourhood from nyc_1;

# 8. write query to show room_type from nyc_1

select room_type from nyc_1;

# 9. write query to show all values of Brooklyn & Manhattan from nyc_1

select * from nyc_1;
select * from nyc_1 where neighbourhood_group = "brooklyn" or neighbourhood_group = "manhattan";

select * from nyc_1 where neighbourhood_group in ('brooklyn','manhattan');

# 10. write query to show unique value of room type from nyc_1

select distinct room_type from nyc_1;

# 11. write query to show maximum price from nyc_2
select * from nyc_2;

select max(price) from nyc_2;

# 12.write query to show minimum price from nyc_2

select min() (price) from nyc_2;

# 13. write query to show average price from nyc_2

select avg(price) from nyc_2; 

# 14.write query to show minimum value of minimum_nights from nyc_2

select min(minimum_nights) from nyc_2;

# 15.write query to show maximum value of minimum_nights from nyc_2

select max(minimum_nights) from nyc_2;

# 16. write query to show average availability_365

select avg(availability_365) from nyc_2;

# 17.write query to show id , availability_365 and all availability_365 value is greater than 300

select id,availability_365 from nyc_2 where availability_365 > 300;

# 18. write query to show count of id where price is in between 300 to 400

select count(id) from nyc_2 where price between 300 and 400; 

# 19. write query to show count of id where minimum_nights spend is less than 5

select count(id) from nyc_2 where minimum_nights < 5;

# 20.write query to show count where minimum_nights spend is greater than 100

select count(id) from nyc_2 where minimum_nights > 100;

# 21. write query to show all data of nyc_1 & nyc_2

select * from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id;

# 22. write query to show host name and price

select host_name, price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id;

# 23. write query to show room_type and price

select room_type, price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id;

# 24. write query to show neighbourhood_group&minimum_nights spend

select neighbourhood_group, minimum_nights  from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id;

# 25. write query to show neighbourhood & availability_365

select neighbourhood, availability_365 from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id;

# 26.write query to show total price by neighbourhood_group

select neighbourhood_group, sum(price) as total_sum from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by neighbourhood_group;

# 27.write query to show maximum price by neighbourhood_group

select neighbourhood_group, max(price) as max_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by neighbourhood_group;

# 28.write query to show maximum night spend by neighbourhood_group

select neighbourhood_group, max(minimum_nights) as max_night_spent from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by neighbourhood_group;


# 29.write query to show maximum reviews_per_month spend by neighbourhood

select neighbourhood_group, round(max(reviews_per_month),2) as max_reviews_per_month from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by neighbourhood_group;

# 30.write query to show maximum price by room type

select room_type, max(price) as max_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by room_type;

# 31.write query to show average number_of_reviews by room_type

select room_type, avg(number_of_reviews) as avg_reviews from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by room_type;

# 32.write query to show average price by room type

select room_type, avg(price) as avg_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by room_type;

# 33.write query to show average night spend by room type

select room_type, avg(minimum_nights) as avg_night_spent from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by room_type;

# 34.write query to show average price by room type but average price is less than 100

select room_type, avg(price) as AVG_PRICE from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by nyc_1.room_type having AVG_PRICE < 100;

# 35.write query to show average night by neighbourhood and average_nights is greater than 5

select neighbourhood, round(avg(minimum_nights),0) as AVG_NIGHT from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by nyc_1.neighbourhood having AVG_NIGHT > 5;

# 36. write query to show all data from nyc_1 and price is greater than 200 using sub-query

select * from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id where nyc_1.id in  
(select id from nyc_2 where nyc_2.price > 200);

# 37. write query to show all values from nyc_2 table and host id is 314941

select * from nyc_2 join nyc_1 on nyc_1.id = nyc_2.id where nyc_1.host_id = 314941;

# 38. Find all pairs of id having the same host id, each pair coming once only.(check with mentor)

select distinct n.id , n.host_id from nyc_1 n, nyc_1 n1 where  n.host_id =  n1.host_id and n.id  <> n1.id  order by host_id;

select distinct id, host_id from nyc_1 where host_id = id order by host_id;

# 39.write sql query to show fetch all records that have the term cozy in name

select * from nyc_1 where name like " %cozy%" ;

# 40. write query to show price host id neighbourhood_group of manhattanneighbourhood_group

select nyc_1.host_id, nyc_1.neighbourhood_group, nyc_2.price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
where neighbourhood_group = 'manhattan';

# 41.write query to show id , host name, neighbourhood and price but only for Upper West Side & Williamsburg neighbourhood also price is greater than 100

select nyc_1.id, nyc_1.host_name, nyc_1.neighbourhood, nyc_2.price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
where neighbourhood in ('upper west side','williamburg')
having nyc_2.price > 100;

# 42.write query to show id , host name, neighbourhood and price for host name Elise and neighbourhood is Bedford-Stuyvesant

select nyc_1.id, nyc_1.host_name, nyc_1.neighbourhood, nyc_2.price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
where host_name = 'elise' and  neighbourhood = 'bedford-stuyvesant';

# 43. write query to show host_name,availability_365,minimum_nights only for 100+ availability_365 and minimum_nights

select nyc_1.host_name, nyc_2.availability_365 , nyc_2.minimum_nights from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
where availability_365 >100;

# 44. write query to show to fetch id ,host_name , number_of_reviews, and reviews_per_month but show only that records where number of reviews are 500+ and review per month is 5+

select nyc_1.id, nyc_1.host_name, nyc_2.number_of_reviews , nyc_2.reviews_per_month  from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
where number_of_reviews > 500 and reviews_per_month >5;

# 45. write query to show neighbourhood_group which have most total number of review

select nyc_1.neighbourhood_group, sum(nyc_2.number_of_reviews) as total_reviews from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
group by neighbourhood_group order by total_reviews desc limit 1;

# 46. write query to show host name which have most cheaper total price

select nyc_1.host_name , sum(nyc_2.price) as total_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by nyc_1.host_name order by total_price asc limit 1;

# 47. write query to show host name which have most costly total price

select nyc_1.host_name , sum(nyc_2.price) as total_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
group by nyc_1.host_name order by total_price desc limit 1;

# 48. write query to show host name which have max price using sub-query

select nyc_1.host_name , nyc_2.price as Max_price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id
where nyc_2.price = (select max(price) from nyc_2) ;

# 49. write query to show neighbourhood_group which price are less than 100

select nyc_1.neighbourhood_group, nyc_2.price from nyc_1 join nyc_2 on nyc_1.id = nyc_2.id 
where nyc_2.price < 100;

# 50. write query to find max price, average availability_365 for each room type and order in ascending by maximum price

select nyc_1.room_type, max(nyc_2.price) as maximum_price, avg(nyc_2.availability_365) as avg_avail from nyc_1 join nyc_2
on nyc_1.id = nyc_2.id group by nyc_1.room_type order by maximum_price asc;




