# relational-databases-lecture

-- ALTER TABLE STATEMENTS

-- ALTER TABLE artist
-- ADD COLUMN member_count INT;

-- ALTER TABLE artist
-- DROP COLUMN member_count;

-- ALTER TABLE artist
-- ALTER name
-- TYPE VARCHAR(250);

-- ALTER TABLE customer
-- RENAME COLUMN last_name
-- TO surname;

-- ALTER TABLE customer
-- RENAME TO people_who_give_me_money;

-- NORMALIZATION, FOREIGN KEYS, AND JOINS

-- INSERT INTO playlist (name)
-- VALUES ('Top Albums 2010-2019');

-- SELECT * FROM playlist WHERE playlist_id = 19;

-- INSERT INTO playlist_track (playlist_id, track_id)
-- VALUES (19, 780);

-- SELECT t.track_id, name, milliseconds 
-- FROM playlist_track pt
-- JOIN track t ON pt.track_id = t.track_id
-- WHERE playlist_id = 19;

-- SELECT * FROM album al
-- JOIN artist ar ON al.artist_id = ar.artist_id;

-- CREATE TABLE secret_tracks(
--   secret_tracks_id SERIAL PRIMARY KEY,
--   track_id INT REFERENCES track(track_id) UNIQUE
-- )

-- INSERT INTO secret_tracks (track_id)
-- VALUES (779);

--THIS IS AN EXAMPLE OF A QUERY THAT WILL FAIL
-- INSERT INTO secret_tracks (track_id)
-- VALUES (5000);

-- SELECT t.track_id, t.name AS track_title, 
-- ar.name AS artist, al.title AS album_title, 
-- t.milliseconds, g.name AS genre
-- FROM secret_tracks st
-- JOIN track t ON t.track_id = st.track_id
-- JOIN album al ON t.album_id = al.album_id
-- JOIN artist ar ON al.artist_id = ar.artist_id
-- JOIN genre g ON g.genre_id = t.genre_id

-- SUB QUERIES

-- SELECT genre_id FROM genre
-- WHERE name IN ('Metal', 'Pop');

-- SELECT * FROM track WHERE genre_id IN (
--   SELECT genre_id FROM genre
-- 	WHERE name IN ('Metal', 'Pop')
-- );
