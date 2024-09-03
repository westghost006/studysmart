# studysmart
Trabajo de Apps Nativas
CREATE TABLE Rol (
    ID_Rol INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(50) UNIQUE
);

INSERT INTO Rol (Nombre) VALUES ('admin'), ('profesor'), ('alumno');

CREATE TABLE Duracion (
    ID_Duracion INT AUTO_INCREMENT PRIMARY KEY,
    Minutos INT UNIQUE
);

INSERT INTO Duracion (Minutos) VALUES (30), (60), (90);

CREATE TABLE Usuario (
    ID_Usuario INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100),
    Apellido VARCHAR(100),
    Email VARCHAR(100) UNIQUE,
    Clave VARCHAR(100),
    Imagen VARCHAR(255),  
    ID_Rol INT,
    FOREIGN KEY (ID_Rol) REFERENCES Rol(ID_Rol)
);

CREATE TABLE Materia (
    ID_Materia INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100)
);

CREATE TABLE Profesor_materia (
    ID_Profesor_materia INT AUTO_INCREMENT PRIMARY KEY,
    ID_Materia INT,
    ID_Usuario INT,
    FOREIGN KEY (ID_Materia) REFERENCES Materia(ID_Materia),
    FOREIGN KEY (ID_Usuario) REFERENCES Usuario(ID_Usuario)
);

CREATE TABLE Dia (
    ID_Dia INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(50) UNIQUE
);

INSERT INTO Dia (Nombre) VALUES ('Lunes'), ('Martes'), ('Miércoles'), ('Jueves'), ('Viernes'), ('Sábado'), ('Domingo');

CREATE TABLE Horario (
    ID_Horario INT AUTO_INCREMENT PRIMARY KEY,
    Hora_inicio TIME,
    Hora_fin TIME
);

CREATE TABLE Calendario_profesor (
    ID_Calendario_profesor INT AUTO_INCREMENT PRIMARY KEY,
    ID_Dia INT,
    ID_Horario INT,
    ID_Profesor INT,
    FOREIGN KEY (ID_Dia) REFERENCES Dia(ID_Dia),
    FOREIGN KEY (ID_Horario) REFERENCES Horario(ID_Horario),
    FOREIGN KEY (ID_Profesor) REFERENCES Usuario(ID_Usuario)
);

CREATE TABLE Clase (
    ID_Clase INT AUTO_INCREMENT PRIMARY KEY,
    Fecha_hora DATETIME,
    Link_encuentro VARCHAR(255),
    ID_Duracion INT,
    ID_Profesor INT,
    ID_Alumno INT,
    FOREIGN KEY (ID_Duracion) REFERENCES Duracion(ID_Duracion),
    FOREIGN KEY (ID_Profesor) REFERENCES Usuario(ID_Usuario),
    FOREIGN KEY (ID_Alumno) REFERENCES Usuario(ID_Usuario)
);
