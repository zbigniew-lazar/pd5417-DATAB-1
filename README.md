# pd5417-DATAB-1
## Wyniki zapytań SQL

### 1. Wyświetlenie wszystkich pacjentów

```sql
SELECT * FROM patients;
```

| id | name | date_of_birth | email | phone_number | weight | height |
|----|------|---------------|--------|-------------|--------|--------|
| 1 | John Doe | 1985-06-15 | john.doe@gmail.com | 1234567890 | 72.5 | 180 |
| 2 | Jane Smith | 1990-03-20 | jane.smith@gmail.com | 987654321 | 60.0 | 165 |
| 3 | Maria Garcia | 1978-12-05 | | 1122334455 | 68.0 | 170 |
| 4 | James Brown | 2000-07-15 | james.brown@yahoo.com | 5566778899 | 80.25 | 175 |
| 5 | Emily Davis | 1995-02-10 | emily.davis@outlook.com | 6677889900 | 55.5 | 160 |

### 2. Pacjenci o masie większej niż 65 kg

```sql
SELECT * FROM patients
WHERE weight > 65;
```

| id | name | date_of_birth | email | phone_number | weight | height |
|----|------|---------------|--------|-------------|--------|--------|
| 1 | John Doe | 1985-06-15 | john.doe@gmail.com | 1234567890 | 72.5 | 180 |
| 3 | Maria Garcia | 1978-12-05 | | 1122334455 | 68.0 | 170 |
| 4 | James Brown | 2000-07-15 | james.brown@yahoo.com | 5566778899 | 80.25 | 175 |

### 3. Pacjenci posortowani według wzrostu malejąco

```sql
SELECT * FROM patients
ORDER BY height DESC;
```

| id | name | date_of_birth | email | phone_number | weight | height |
|----|------|---------------|--------|-------------|--------|--------|
| 1 | John Doe | 1985-06-15 | john.doe@gmail.com | 1234567890 | 72.5 | 180 |
| 4 | James Brown | 2000-07-15 | james.brown@yahoo.com | 5566778899 | 80.25 | 175 |
| 3 | Maria Garcia | 1978-12-05 | | 1122334455 | 68.0 | 170 |
| 2 | Jane Smith | 1990-03-20 | jane.smith@gmail.com | 987654321 | 60.0 | 165 |
| 5 | Emily Davis | 1995-02-10 | emily.davis@outlook.com | 6677889900 | 55.5 | 160 |

### 4. Dwa ostatnie rekordy tabeli

```sql
SELECT *
FROM patients
ORDER BY id DESC
LIMIT 2;
```

| id | name | date_of_birth | email | phone_number | weight | height |
|----|------|---------------|--------|-------------|--------|--------|
| 5 | Emily Davis | 1995-02-10 | emily.davis@outlook.com | 6677889900 | 55.5 | 160 |
| 4 | James Brown | 2000-07-15 | james.brown@yahoo.com | 5566778899 | 80.25 | 175 |
