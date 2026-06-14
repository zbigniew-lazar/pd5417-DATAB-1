# pd5417-DATAB-1

## Opis projektu

Celem zadania było praktyczne wykorzystanie podstawowych poleceń SQL w systemie MySQL v5.7. W ramach projektu utworzono tabelę pacjentów, dodano przykładowe dane, wykonano zapytania wyszukujące oraz przeprowadzono modyfikacje danych i struktury tabeli.

---

# Definicja tabeli i dane testowe

## Schemat bazy danych

```sql
CREATE TABLE patients (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    date_of_birth DATE,
    email VARCHAR(255),
    phone_number VARCHAR(20),
    weight DECIMAL(5,2),
    height INT
);
```

## Wstawienie danych

```sql
INSERT INTO patients (id, name, date_of_birth, email, phone_number, weight, height)
VALUES
(1, 'John Doe', '1985-06-15', 'john.doe@gmail.com', '1234567890', 72.50, 180),
(2, 'Jane Smith', '1990-03-20', 'jane.smith@gmail.com', '987654321', 60.00, 165),
(3, 'Maria Garcia', '1978-12-05', NULL, '1122334455', 68.00, 170),
(4, 'James Brown', '2000-07-15', 'james.brown@yahoo.com', '5566778899', 80.25, 175),
(5, 'Emily Davis', '1995-02-10', 'emily.davis@outlook.com', '6677889900', 55.50, 160);
```

---

# Wyniki zapytań SQL

## 1. Wyświetlenie wszystkich pacjentów

```sql
SELECT * FROM patients;
```

| id | name         | date_of_birth | email                                                     | phone_number | weight | height |
| -- | ------------ | ------------- | --------------------------------------------------------- | ------------ | ------ | ------ |
| 1  | John Doe     | 1985-06-15    | [john.doe@gmail.com](mailto:john.doe@gmail.com)           | 1234567890   | 72.5   | 180    |
| 2  | Jane Smith   | 1990-03-20    | [jane.smith@gmail.com](mailto:jane.smith@gmail.com)       | 987654321    | 60.0   | 165    |
| 3  | Maria Garcia | 1978-12-05    | NULL                                                      | 1122334455   | 68.0   | 170    |
| 4  | James Brown  | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com)     | 5566778899   | 80.25  | 175    |
| 5  | Emily Davis  | 1995-02-10    | [emily.davis@outlook.com](mailto:emily.davis@outlook.com) | 6677889900   | 55.5   | 160    |

---

## 2. Pacjenci o masie większej niż 65 kg

```sql
SELECT *
FROM patients
WHERE weight > 65;
```

| id | name         | date_of_birth | email                                                 | phone_number | weight | height |
| -- | ------------ | ------------- | ----------------------------------------------------- | ------------ | ------ | ------ |
| 1  | John Doe     | 1985-06-15    | [john.doe@gmail.com](mailto:john.doe@gmail.com)       | 1234567890   | 72.5   | 180    |
| 3  | Maria Garcia | 1978-12-05    | NULL                                                  | 1122334455   | 68.0   | 170    |
| 4  | James Brown  | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com) | 5566778899   | 80.25  | 175    |

---

## 3. Pacjenci posortowani według wzrostu malejąco

```sql
SELECT *
FROM patients
ORDER BY height DESC;
```

| id | name         | date_of_birth | email                                                     | phone_number | weight | height |
| -- | ------------ | ------------- | --------------------------------------------------------- | ------------ | ------ | ------ |
| 1  | John Doe     | 1985-06-15    | [john.doe@gmail.com](mailto:john.doe@gmail.com)           | 1234567890   | 72.5   | 180    |
| 4  | James Brown  | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com)     | 5566778899   | 80.25  | 175    |
| 3  | Maria Garcia | 1978-12-05    | NULL                                                      | 1122334455   | 68.0   | 170    |
| 2  | Jane Smith   | 1990-03-20    | [jane.smith@gmail.com](mailto:jane.smith@gmail.com)       | 987654321    | 60.0   | 165    |
| 5  | Emily Davis  | 1995-02-10    | [emily.davis@outlook.com](mailto:emily.davis@outlook.com) | 6677889900   | 55.5   | 160    |

---

## 4. Dwa ostatnie rekordy tabeli

```sql
SELECT *
FROM patients
ORDER BY id DESC
LIMIT 2 OFFSET 0;
```

| id | name        | date_of_birth | email                                                     | phone_number | weight | height |
| -- | ----------- | ------------- | --------------------------------------------------------- | ------------ | ------ | ------ |
| 5  | Emily Davis | 1995-02-10    | [emily.davis@outlook.com](mailto:emily.davis@outlook.com) | 6677889900   | 55.5   | 160    |
| 4  | James Brown | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com)     | 5566778899   | 80.25  | 175    |

---

# Modyfikacja danych i struktury tabeli

W kolejnym etapie wykonano operacje aktualizacji danych, usunięcia rekordu oraz modyfikacji struktury tabeli.

## Wykonane polecenia SQL

```sql
UPDATE patients
SET email = 'john.updated@gmail.com'
WHERE name = 'John Doe';

DELETE FROM patients
WHERE id = 3;

ALTER TABLE patients
ADD blood_type CHAR(3);

UPDATE patients
SET blood_type = 'O+'
WHERE name = 'John Doe';

UPDATE patients
SET blood_type = 'AB+'
WHERE name = 'Jane Smith';

UPDATE patients
SET blood_type = 'A-'
WHERE name = 'James Brown';

UPDATE patients
SET blood_type = 'B+'
WHERE name = 'Emily Davis';
```

---

# Wyniki po modyfikacji danych

## 1. Wszystkie rekordy po modyfikacji

```sql
SELECT * FROM patients;
```

| id | name        | date_of_birth | email                                                     | phone_number | weight | height | blood_type |
| -- | ----------- | ------------- | --------------------------------------------------------- | ------------ | ------ | ------ | ---------- |
| 1  | John Doe    | 1985-06-15    | [john.updated@gmail.com](mailto:john.updated@gmail.com)   | 1234567890   | 72.5   | 180    | O+         |
| 2  | Jane Smith  | 1990-03-20    | [jane.smith@gmail.com](mailto:jane.smith@gmail.com)       | 987654321    | 60.0   | 165    | AB+        |
| 4  | James Brown | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com)     | 5566778899   | 80.25  | 175    | A-         |
| 5  | Emily Davis | 1995-02-10    | [emily.davis@outlook.com](mailto:emily.davis@outlook.com) | 6677889900   | 55.5   | 160    | B+         |

---

## 2. Dwa ostatnie rekordy po modyfikacji

```sql
SELECT *
FROM patients
ORDER BY id DESC
LIMIT 2 OFFSET 0;
```

| id | name        | date_of_birth | email                                                     | phone_number | weight | height | blood_type |
| -- | ----------- | ------------- | --------------------------------------------------------- | ------------ | ------ | ------ | ---------- |
| 5  | Emily Davis | 1995-02-10    | [emily.davis@outlook.com](mailto:emily.davis@outlook.com) | 6677889900   | 55.5   | 160    | B+         |
| 4  | James Brown | 2000-07-15    | [james.brown@yahoo.com](mailto:james.brown@yahoo.com)     | 5566778899   | 80.25  | 175    | A-         |

---

Autor: Zbigniew Lazar
