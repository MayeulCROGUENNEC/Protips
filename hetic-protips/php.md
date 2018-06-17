# C KOA

```php
$stmt = $conn->prepare($sql);
$stmt->execute();


$stmt = $conn->prepare($sql);
```

```php
while (false !== $row = $stmt->fetch(PDO::FETCH_ASSOC)) :
...
endwhile;
```

```php
SET NAMES 'utf8';
```
___

##MySQL (KandT)

* Créer base de données
```sql
CREATE SCHEMA `KandT`
DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

* Créer table
```sql
CREATE TABLE `KandT`.`page` (
   `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
   `title` VARCHAR(110) NOT NULL,
   `h1` VARCHAR(70) NOT NULL,
   `paragraphe` VARCHAR(3000) NOT NULL,
   `span-class` VARCHAR(400) NOT NULL,
   `span-text` VARCHAR(50) NOT NULL,
   `img-alt` VARCHAR(100) NOT NULL,
   `img-src` VARCHAR(2048) NOT NULL,
   `nav-title` VARCHAR(50) NOT NULL,
   `slug` VARCHAR(50) NOT NULL,
   PRIMARY KEY (`id`)
);
```

* Insérer contenu dans la table
```sql
INSERT INTO
   `page`
   (`id`, `title`, `h1`, `paragraphe`, `span-class`, `span-text`, `img-alt`, `img-src`, `nav-title`, `slug`)
VALUES
   (NULL, 'Nier', 'Nier', `C 1 J-RPG`, `label-primary`, `Robot`, `nierA`, `nieremil.jpg`, `nier`)
;
```
