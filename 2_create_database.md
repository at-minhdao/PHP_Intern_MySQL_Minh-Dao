### 1. Tạo database như hình trên (sau khi tạo thì import database)
- Create database
```mysql
  CREATE DATABASE `train_mysql` DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
```
- Create table `user`
```mysql
  CREATE TABLE `user` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
    `full_name` VARCHAR(255),
    `email` VARCHAR(255),
    `rank` TINYINT(4),
    `is_active` TINYINT(1),
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY(`id`)
  );
```