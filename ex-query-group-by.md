# EX QUERY CON GROUP BY

Esercizio di oggi: DB University

nome repo: db-university

Dopo aver creato un nuovo database nel vostro phpMyAdmin e aver importato lo schema allegato, eseguite le query del file allegato.

Cosa consegnare?

Dopo aver testato le vostre query con phpMyAdmin, riportatele in un file txt e caricatelo nella vostra repo.

### traccie

1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

### soluzioni

1.

```sql
SELECT COUNT(*) AS `freshman`, YEAR(`enrolment_date`) AS `enrolment_year` FROM `students` GROUP BY YEAR(`enrolment_date`);
```

(4)

2.

```sql
SELECT COUNT(*) AS `teacher`, `office_address` FROM `teachers` GROUP BY `office_address`;
```

(29)

3.

```sql
SELECT `exam_id`, AVG(`vote`) AS `average_vote` FROM `exam_student` GROUP BY `exam_id`;
```

(4078)

4.

```sql
SELECT `department_id` AS `department`, COUNT(*) AS `degree` FROM `degrees` GROUP BY `department_id`;
```

(12)

```

```
