# Week 3

## Exercises 2: Single Table Queries

### Question 1:
select *  from goal;

![Screenshot 2024-09-12 151240.png](img%2FScreenshot%202024-09-12%20151240.png)

### Question 2:
select name, type from airport where iso_country = "FI";

![Screenshot 2024-09-12 152911.png](img%2FScreenshot%202024-09-12%20152911.png)

### Question 3:
select name from airport where iso_country = "FI" order by name;

![Screenshot 2024-09-12 153535.png](img%2FScreenshot%202024-09-12%20153535.png)

### Question 4:
select name, type from airport where iso_country = "FI" order by type, name;

![Screenshot 2024-09-12 171058.png](img%2FScreenshot%202024-09-12%20171058.png)

### Question 5:
select name from country where name like "F%";

![Screenshot 2024-09-12 171449.png](img%2FScreenshot%202024-09-12%20171449.png)

### Question 6:
select name from country where name like "%F%";

![Screenshot 2024-09-12 171709.png](img%2FScreenshot%202024-09-12%20171709.png)

### Question 7
select location from game where screen_name = "Vesa";

![Screenshot 2024-09-12 172044.png](img%2FScreenshot%202024-09-12%20172044.png)

### Question 8:
select co2_consumed from game where screen_name = "Ilkka";

![Screenshot 2024-09-12 172642.png](img%2FScreenshot%202024-09-12%20172642.png)

### Question 9:
select distinct co2_budget from game;

![Screenshot 2024-09-12 172828.png](img%2FScreenshot%202024-09-12%20172828.png)

### Question 10:
select screen_name, co2_budget, co2_consumed, co2_budget - co2_consumed as co2_left from game where screen_name = "Ilkka";

![Screenshot 2024-09-12 173650.png](img%2FScreenshot%202024-09-12%20173650.png)

## Exercises 3: Multiple Table Queries

### Question 1:
select country.name as "country name", airport.name as "airport name" from airport, country where airport.iso_country = country.iso_country and country.name = "Iceland";

![Screenshot 2024-09-12 214817.png](img%2FScreenshot%202024-09-12%20214817.png)

### Question 2:
select airport.name as "airport name" from airport, country where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";

![Screenshot 2024-09-12 215514.png](img%2FScreenshot%202024-09-12%20215514.png)

### Question 3:
select country.name as country_name, airport.name as airport_name from airport, country where airport.iso_country = country.iso_country and country.continent = "an";

![Screenshot 2024-09-12 220131.png](img%2FScreenshot%202024-09-12%20220131.png)

### Question 4:
select elevation_ft from airport, game where location = ident and screen_name = "Heini";

![Screenshot 2024-09-12 220555.png](img%2FScreenshot%202024-09-12%20220555.png)

### Question 5:
select elevation_ft * 0.3048 as elevation_m from airport, game where location = ident and screen_name = "Heini";

![Screenshot 2024-09-12 221036.png](img%2FScreenshot%202024-09-12%20221036.png)

### Question 6:
select name from airport, game where location = ident and screen_name = "Ilkka";

![Screenshot 2024-09-12 221325.png](img%2FScreenshot%202024-09-12%20221325.png)

### Question 7:
select country.name from airport, country, game where airport.iso_country = country.iso_country and location = ident and screen_name = "Ilkka";

![Screenshot 2024-09-12 221808.png](img%2FScreenshot%202024-09-12%20221808.png)

### Question 8:
select name from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini";

![Screenshot 2024-09-12 222256.png](img%2FScreenshot%202024-09-12%20222256.png)

### Question 9:
select airport.name from airport, game, goal, goal_reached where ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";

![Screenshot 2024-09-12 222716.png](img%2FScreenshot%202024-09-12%20222716.png)

### Question 10:
select country.name from country, airport, game, goal, goal_reached where airport.iso_country = country.iso_country and ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";

![Screenshot 2024-09-12 214023.png](img%2FScreenshot%202024-09-12%20214023.png)

# Week 4:

## Exercises 4: Join

### Question 1:
select country.name as "country name", airport.name as "airport name" from country inner join airport on airport.iso_country = country.iso_country where country.name = "Finland" and scheduled_service = "yes";

![Screenshot 2024-09-13 084256.png](img%2FScreenshot%202024-09-13%20084256.png)

### Question 2:
select screen_name, airport.name from game inner join airport on location = ident;

![Screenshot 2024-09-13 085546.png](img%2FScreenshot%202024-09-13%20085546.png)

### Question 3:
select screen_name, country.name from game inner join airport on location = ident inner join country on airport.iso_country = country.iso_country;

![Screenshot 2024-09-13 090137.png](img%2FScreenshot%202024-09-13%20090137.png)

### Question 4:
select airport.name, screen_name from airport left join game on ident = location where name like "%Hels%";

![Screenshot 2024-09-13 091034.png](img%2FScreenshot%202024-09-13%20091034.png)

### Question 5:
select name, screen_name from goal left join goal_reached on goal.id = goal_id left join game on game.id = game_id;

![Screenshot 2024-09-13 091314.png](img%2FScreenshot%202024-09-13%20091314.png)

## Exercises 5: Subqueries

### Question 1:
select name from country where iso_country in (select iso_country from airport where name like "Satsuma%");

![Screenshot 2024-09-13 092935.png](img%2FScreenshot%202024-09-13%20092935.png)

### Question 2:
select name from airport where iso_country in (select iso_country from country where name = "Monaco");

![Screenshot 2024-09-13 093604.png](img%2FScreenshot%202024-09-13%20093604.png)

### Question 3:
select screen_name from game where id in (select game_id from goal_reached where goal_id in (select id from goal where name = "CLOUDS"));

![Screenshot 2024-09-13 095645.png](img%2FScreenshot%202024-09-13%20095645.png)

### Question 4:
select name from country where iso_country not in (select iso_country from airport);

![Screenshot 2024-09-13 100124.png](img%2FScreenshot%202024-09-13%20100124.png)

### Question 5:
select name from goal where id not in (select goal.id from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini);

![Screenshot 2024-09-13 100512.png](img%2FScreenshot%202024-09-13%20100512.png)

## Exercises 6: Aggregate Queries

### Question 1:
select max(elevation_ft) from airport;

![Screenshot 2024-09-13 103243.png](img%2FScreenshot%202024-09-13%20103243.png)

### Question 2:
select continent, count (*) from country group by continent;

![Screenshot 2024-09-13 103905.png](img%2FScreenshot%202024-09-13%20103905.png)

### Question 3:
select screen_name, count(*) from game, goal_reached where id = game_id group by screen_name;

![Screenshot 2024-09-13 104135.png](img%2FScreenshot%202024-09-13%20104135.png)

### Question 4:
select screen_name from game where co2_consumed in (select min(co2_consumed) from game);

![Screenshot 2024-09-13 104605.png](img%2FScreenshot%202024-09-13%20104605.png)

### Question 5:
select country.name, count(*) from airport, country where airport.iso_country = country.iso_country group by country.iso_country order by count(*) desc limit 50;

![Screenshot 2024-09-13 105237.png](img%2FScreenshot%202024-09-13%20105237.png)

### Question 6:
select country.name from airport, country where airport, country where airport.iso_country = country.iso_country group by country.iso_country having count(*) > 1000;

![Screenshot 2024-09-13 110023.png](img%2FScreenshot%202024-09-13%20110023.png)

### Question 7:
select name from airport where elevation_ft in (select max(elevation_ft) from airport);

![Screenshot 2024-09-13 110450.png](img%2FScreenshot%202024-09-13%20110450.png)

### Question 8:
select country.name from airport, country where airport.iso_country = country.iso_country and elevation_ft in (select max(elevation_ft) from airport);

![Screenshot 2024-09-13 110828.png](img%2FScreenshot%202024-09-13%20110828.png)

### Question 9:
select count(*) from game, goal_reached where id = game_id and screen_name = "Vesa";

![Screenshot 2024-09-13 111240.png](img%2FScreenshot%202024-09-13%20111240.png)

### Question 10:
select name from airport where latitude_deg in (select min(latitude_deg) from airport);

![Screenshot 2024-09-13 111755.png](img%2FScreenshot%202024-09-13%20111755.png)

## Exercise 7: Update Queries

### Question 1: 
update game 
set location = (select ident from airport where name = "Nottingham Airport"),
co2_consumed = co2_consumed + 500 where screen_name = "Vesa"
;

select * from game;

![Screenshot 2024-09-15 103725.png](img%2FScreenshot%202024-09-15%20103725.png)

### Question 3:
DELETE FROM goal_reached;
SELECT * FROM goal_reached;

![Screenshot 2024-09-15 104458.png](img%2FScreenshot%202024-09-15%20104458.png)

### Question 4:
DELETE FROM game;
SELECT * FROM game;

![Screenshot 2024-09-15 104735.png](img%2FScreenshot%202024-09-15%20104735.png)


