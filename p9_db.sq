-- Práctica 9: Pase de Lista con GPS
-- Base de datos: asistencia_gps

CREATE DATABASE IF NOT EXISTS asistencia_gps
  CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE asistencia_gps;

-- Usuarios (la contraseña se guarda como hash MD5)
-- role: 'student' (por defecto) o 'admin' (opcional de roles)
CREATE TABLE IF NOT EXISTS users (
  id INT(11) NOT NULL AUTO_INCREMENT,
  username VARCHAR(50) NOT NULL,
  password VARCHAR(50) NOT NULL,
  role VARCHAR(20) NOT NULL DEFAULT 'student',
  PRIMARY KEY (id),
  UNIQUE KEY username (username)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Registros de asistencia con coordenadas GPS y dirección
CREATE TABLE IF NOT EXISTS attendance (
  id INT(11) NOT NULL AUTO_INCREMENT,
  user_id INT(11) NOT NULL,
  latitude DOUBLE NOT NULL,
  longitude DOUBLE NOT NULL,
  address TEXT NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (id),
  KEY user_id (user_id),
  CONSTRAINT attendance_ibfk_1 FOREIGN KEY (user_id)
    REFERENCES users (id) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Usuario administrador de prueba (usuario: admin / contraseña: admin123)
INSERT IGNORE INTO users (username, password, role)
VALUES ('admin', MD5('admin123'), 'admin');

-- ALTER TABLE users ADD COLUMN role VARCHAR(20) NOT NULL DEFAULT 'student';
-- UPDATE users SET role='admin' WHERE username='TU_USUARIO';