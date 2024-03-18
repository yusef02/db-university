# EX QUERY CON JOIN

### traccie

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

### soluzioni

1.

```sql
SELECT DISTINCT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` LIKE `degrees`.`id` INNER JOIN `courses` ON `degrees`.`id` LIKE `courses`.`degree_id` WHERE `degrees`.`name` LIKE 'Corso di Laurea in Economia';
```

2.

```sql
SELECT * FROM `courses` INNER JOIN `degrees` ON `degree_id` LIKE `degrees`.`id` INNER JOIN `departments`ON `degrees`.`department_id` LIKE departments`.`id`WHERE`departments`.`name`LIKE 'Dipartimento di Neuroscienze' AND`degrees`.`level` LIKE 'magistrale';
```

3.

```sql
SELECT * FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id` LIKE `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` LIKE `teachers`.`id` WHERE `teachers`.`name` LIKE 'Fulvio' AND `teachers`.`surname` LIKE 'Amato';
```

4.

```sql
SELECT `students`.`name`, `students`.`surname`, `degrees`.`name`, `departments`.`name` FROM `students` INNER JOIN `degrees` ON `degrees`.`id` LIKE `students`.`degree_id` INNER JOIN `departments` ON `departments`.`id` LIKE `degrees`.`department_id`;
```

5.

```sql
SELECT `degrees`.`name` AS `degree`, `courses`.`name` AS `course`, `teachers`.`name` AS `teacher_name`,`teachers`.`surname` AS `teacher_surname` FROM `degrees` INNER JOIN `courses` ON `courses`.`degree_id` LIKE `degrees`.`id` INNER JOIN `course_teacher` ON `courses`.`id` LIKE `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` LIKE `teachers`.`id`;
```

6.

```sql
SELECT * FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` LIKE `course_teacher`.`teacher_id` INNER JOIN `courses` ON `courses`.`id` LIKE `course_teacher`.`course_id` INNER JOIN `degrees` ON `degrees`.`id` LIKE `courses`.`degree_id` INNER JOIN `departments` ON `departments`.`id` LIKE `degrees`.`department_id` WHERE `departments`.`name` LIKE 'Dipartimento di matematica';
```
