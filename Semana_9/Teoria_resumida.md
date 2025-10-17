# Funciones y Procedimientos Almacenados en MySQL

> Basado en el material de **Emilio Rojas Soria** – *Funciones y Procedimientos MySQL*

---

## 📌 Introducción a Rutinas

En MySQL, una **rutina** es un bloque de código SQL reutilizable que se almacena directamente en la base de datos. Existen dos tipos principales:

- **Funciones almacenadas (`FUNCTION`)**:  
  - Retornan **un único valor**.  
  - Se pueden usar **dentro de expresiones SQL** (por ejemplo, en `SELECT`, `WHERE`, etc.).  
  - Se invocan con `SELECT`.

- **Procedimientos almacenados (`PROCEDURE`)**:  
  - **No retornan un valor directamente**, pero pueden devolver resultados mediante:
    - Parámetros `OUT` o `INOUT`.
    - Sentencias `SELECT` internas.
  - Se invocan con `CALL`.

### ✅ Beneficios de usar rutinas
- **Reutilización de código**
- **Seguridad y control de acceso**
- **Reducción del tráfico de red** entre la aplicación y la base de datos

---

## 🛠️ Sintaxis Básica

### 🔹 Crear una Función

```sql
DELIMITER //
CREATE FUNCTION fn_multiplicar(a INT, b INT)
RETURNS INT
DETERMINISTIC
BEGIN
  DECLARE resultado INT;
  SET resultado = a * b;
  RETURN resultado;
END //
DELIMITER ;


-- Usa RETURNS para especificar el tipo de retorno.
-- Usa RETURN para devolver el valor.
-- DETERMINISTIC indica que siempre devuelve el mismo resultado con los mismos parámetros.

```

### 🔹 Crear un Procedimiento almacenado
```sql
CREATE PROCEDURE sp_obtener_nombre (
  IN p_id INT,
  OUT p_nombre VARCHAR(100)
)
BEGIN
  SELECT nombre INTO p_nombre
  FROM clientes
  WHERE id = p_id;
END

```
