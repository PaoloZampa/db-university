# Query 2 JOIN

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT students.id, students.name, degrees.name
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT degrees.* , departments.name AS department_name, degrees.level
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE degrees.level = 'Magistrale'
AND departments.name = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT course_teacher.teacher_id, course_teacher.course_id, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM course_teacher
JOIN teachers ON course_teacher.teacher_id = teachers.id
JOIN courses ON course_teacher.course_id = courses.id
WHERE course_teacher.teacher_id = 44
AND teachers.name = 'Fulvio'
AND teachers.surname = 'Amato';

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT students.surname AS student_surname, students.name AS student_name, students.date_of_birth, degrees.name AS degree_name, degrees.level, degrees.email , departments.name AS department_name
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname, students.name;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT courses.name AS course_name, teachers.name AS teacher_name, teachers.surname as teacher_surname, degrees.name AS degree_name
FROM course_teacher
JOIN courses ON course_teacher.course_id = courses.id
JOIN teachers ON course_teacher.teacher_id = teachers.id
JOIN degrees ON courses.degree_id = degrees.id
ORDER BY degrees.name;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT teachers.name as teacher_name, teachers.surname AS teacher_surname, departments.name AS department_name
FROM course_teacher
JOIN courses ON course_teacher.course_id = courses.id
JOIN teachers ON course_teacher.teacher_id = teachers.id
JOIN degrees ON courses.degree_id = degrees.id
JOIN departments on degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
superare ciascuno dei suoi esami