# SQL Homework

The Glasgow Film Theatre are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'
```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:
```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.
  SELECT * FROM movies;
  returned a table showing the id, title, year, and show time for all 18 movies.

2. Return ONLY the name column from the 'people' table
  SELECT name FROM people;
  returned a list of the names of the guests - 19 rows so 19 names

3. Oops! Someone at CodeClan HQ spelled Jean's name wrong! Change it to reflect the proper spelling ('Gene BaMaung' should be 'Jean BaMaung').
  UPDATE people SET name = 'Jean BaMaung' WHERE name = 'Gene BaMaung';
  SELECT name FROM people;
  returned an edited list of people with Jean BaMaung at the bottom as she was the last edited entry. Used the SELECT function to check update had worked correctly

4. Return ONLY your name from the 'people' table.
  SELECT name FROM people WHERE name = 'Christine Lester';
  returned my name - note, please change this to Christie, thanks!

5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.
  DELETE FROM movies WHERE title = 'Batman Begins';
  SELECT * FROM movies;
  returned a list of the films minus Batman Begins

6. Create a new entry in the 'people' table with the name of one of the instructors.
  INSERT INTO people (name) VALUES ('Alan Russell');
  SELECT name FROM people;
  returned an updated list of names that now includes Alan

7. Jeff Bridges has decided to hijack our movie evening, Remove him from the table of people.

No, Jeff Bridges is always welcome at G4 Movie nights!

DELETE FROM people WHERE name = 'Jeff Bridges';
SELECT name FROM people;

8. The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this. (The year should be 2018)
  INSERT INTO movies (title, year, show_time) VALUES ('Avengers: Infinity War', 2018, '00:00');
  SELECT * FROM movies;
  returns an updated list of films in which the last entry is Avengers Infinity War


9. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 15:30 to 20:00
  UPDATE movies SET show_time = '23:00' WHERE title = 'Guardians of the Galaxy 2';
  SELECT * FROM movies;
  returns a list of films with the show times updated


## Extension

1. Research how to delete multiple entries from your table in a single command.
DELETE FROM movies
WHERE movie IN (SELECT movie FROM movies WHERE year = '2008');

this will delete all films from 2008

There are also ways to do this using ids

DELETE FROM movies
WHERE movie IN (SELECT movie FROM movies WHERE id = 1, 3, 7);

this will delete the Ironman films, which is good because Ironman sucks.
