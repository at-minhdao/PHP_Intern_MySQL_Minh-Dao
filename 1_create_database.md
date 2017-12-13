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
- Create table `category`
```mysql
CREATE TABLE `category` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `title` VARCHAR(255),
  `description` VARCHAR(255),
  PRIMARY KEY(`id`)
);
```
- Create table `news`
```mysql
CREATE TABLE `news` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `category_id` INT(11) NOT NULL,
  `title` VARCHAR(255),
  `view` INT(11),
  `is_active` TINYINT(1),
  `content` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT 0 ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`category_id`) REFERENCES category(id)
);
```
- Create table `comment`
```mysql
CREATE TABLE `comment` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
  `target_table` VARCHAR(20),
  `target_id` INT(11),
  `user_id` INT(11) NOT NULL,
  `comment` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT 0 ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`user_id`) REFERENCES user(id)
);
```
- Create table `follow`
```mysql
CREATE TABLE `follow` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
  `from_user_id` INT(11) NOT NULL,
  `to_user_id` INT(11),
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`from_user_id`) REFERENCES user(id)
);
```
- Create table `blog`
```mysql
CREATE TABLE `blog` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
  `category_id` INT(11) NOT NULL,
  `user_id` INT(11) NOT NULL,
  `title` VARCHAR(255),
  `view` INT(11),
  `is_active` TINYINT(1),
  `content` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT 0 ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`category_id`) REFERENCES category(`id`),
  FOREIGN KEY (`user_id`) REFERENCES user(`id`)
);
```
