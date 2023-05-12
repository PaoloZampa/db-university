# QUERY

1. Selezionare tutti gli studenti nati nel 1990 (160)
mysql> select *
    -> FROM students
    -> WHERE YEAR(date_of_birth) = 1990;
    160 rows in set (0.00 sec)

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
mysql> SELECT *
    -> FROM courses
    -> WHERE cfu > 10;
    479 rows in set (0.00 sec)

3. Selezionare tutti gli studenti che hanno più di 30 anni
mysql> SELECT *
    -> FROM students
    -> WHERE TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) > 30;
    3392 rows in set (0.01 sec)

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
mysql> SELECT *     
    -> FROM courses          
    -> WHERE year = 1 AND period = 'I semestre';
    286 rows in set (0.00 sec)

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
mysql> SELECT *
    -> FROM exams
    -> WHERE date = '2020-06-20' AND hour > '14:00:00';
    21 rows in set (0.00 sec)

6. Selezionare tutti i corsi di laurea magistrale (38)
mysql> SELECT *
    -> FROM degrees
    -> WHERE level = 'magistrale';
    38 rows in set (0.00 sec)

7. Da quanti dipartimenti è composta l'università? (12)
mysql> DESCTRIBE departments;
    -> SELECT id FROM departments;
    12 rows in set (0.00 sec)

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
mysql> SELECT phone    
    -> FROM teachers
    -> WHERE phone IS NOT NULL;
    50 rows in set (0.00 sec)


# database intro library
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni.
Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.diagrams.net/ per la creazione dello schema.
Esportare quindi il diagramma in jpg e caricarlo nella repo. (modificato) 


## data Types:

- strings: [varchar(number), char(number), text, longtext]
- numbers: [tinyint, small/medium int, int, bigint]
- decimals: [float(i, d), duble(i,,d), decimal(i,d)]
- date: [datatime, date, year, time, timestamp]

## attributes:

- NULL/ NOTNULLL
- DEFOULT
- AUTO_INCREMENT
- UNIQUE

## entity:
- dipartimenti
- corsi_di_laurea
    - ?materie?
- insegnanti
- appelli_esame 
- studenti 


## table:
- dipartimento one_to_many corsi_di_laure
- corsi_di_laure many_to_many materie
- materie many_to_many insegnanti
- materie one_to_many appelli_esame
- studenti many_to_many appelli_esame(voto d'esame)
- studneti one_to_many corsi_di_laurea
- 




## relationships:








## Table name: books
## columns: 


