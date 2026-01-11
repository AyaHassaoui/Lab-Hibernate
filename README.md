
---

# TP Hibernate

## 1. Introduction

L’objectif de ce travail pratique est de mettre en œuvre une application Java basée sur **Hibernate ORM** pour gérer la persistance des données dans une base **MySQL**.
Ce projet permet de comprendre le principe du mapping objet–relationnel et l’implémentation d’une couche DAO pour manipuler les données de manière abstraite.
<img width="373" height="530" alt="image" src="https://github.com/user-attachments/assets/3127600f-be0a-472f-b3ca-fca3234e7d13" />

---

## 2. Environnement de Travail

| Outil / Technologie | Version       |
| ------------------- | ------------- |
| Java JDK            | 17            |
| Maven               | 3.x           |
| Hibernate ORM       | 6.x           |
| MySQL               | 8.x           |
| IDE                 | IntelliJ IDEA |
| Système             | Windows 11    |

---

## 3. Architecture du Projet

Le projet est structuré selon une architecture modulaire :

```
src/main/java
 ├── com.example       → Classe principale App
 ├── dao               → Interface IDao
 ├── entities          → Classes Machine, Salle
 ├── services          → MachineService, SalleService
 └── util              → HibernateUtil
src/main/resources
 └── hibernate.cfg.xml → Configuration Hibernate
src/test/java
 └── Tests unitaires (MachineServiceTest, SalleServiceTest)
```

---

## 4. Description des Composants

### 4.1 Entités

* **Machine** : représente une machine avec :

  * id
  * référence
  * date d’achat
  * salle associée

* **Salle** : représente une salle avec :

  * id
  * code

Ces classes sont annotées avec `@Entity`, `@Id`, `@GeneratedValue`, `@ManyToOne`.

---

### 4.2 Couche DAO

Interface générique :

```java
public interface IDao<T> {
    boolean create(T o);
    boolean update(T o);
    boolean delete(T o);
    T findById(int id);
    List<T> findAll();
}
```

---

### 4.3 Services

* **MachineService**
* **SalleService**

Ils implémentent les méthodes CRUD via Hibernate SessionFactory.

---

### 4.4 HibernateUtil

Cette classe permet de créer une instance unique de `SessionFactory` à partir du fichier `hibernate.cfg.xml`.

---

## 5. Configuration Hibernate

Le fichier `hibernate.cfg.xml` contient :

* paramètres de connexion MySQL
* dialecte Hibernate
* mapping des classes Machine et Salle
* mode `update` pour la création automatique des tables

---

## 6. Tests et Exécution

Les classes de test exécutent automatiquement :

* l’insertion des salles
* l’insertion des machines
* l’affichage des données
* la mise à jour et la suppression

Le résultat montre :
<img width="1471" height="722" alt="image" src="https://github.com/user-attachments/assets/bc57aaee-949b-48ca-9c27-476cd22fe603" />

<img width="1457" height="647" alt="image" src="https://github.com/user-attachments/assets/a7976aaf-7c35-40a3-a7a6-5fac8bbc6cd0" />



---

**Réalisé par :**
HASSAOUI Aya

**Encadré par :**
Pr. Mohamed LACHGAR



---

