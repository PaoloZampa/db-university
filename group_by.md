# Query 3 GROUP BY

1. Contare quanti iscritti ci sono stati ogni anno
SELECT YEAR(enrolment_date) AS iscription_year, COUNT(*) AS all_subscribers
FROM students
GROUP BY YEAR(enrolment_date);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT office_address, COUNT(*) AS all_teachers
FROM teachers
GROUP BY office_address;

3. Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(vote) AS average_value, exam_id
FROM exam_student
GROUP BY exam_id;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT departments.name AS departments_name, COUNT(*) AS all_courses
FROM degrees
JOIN departments ON degrees.department_id = departments.id
GROUP BY departments.name;
