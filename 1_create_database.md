### 1. Tạo database như hình trên (sau khi tạo thì import database)
-- Create database
  CREATE DATABASE `train_mysql` DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;

-- Create table `user`
CREATE TABLE IF NOT EXISTS `user` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `full_name` VARCHAR(255),
  `email` VARCHAR(255),
  `rank` TINYINT(4),
  `is_active` TINYINT(1),
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`)
);

-- Create table `category`
CREATE TABLE IF NOT EXISTS `category` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `title` VARCHAR(255),
  `description` VARCHAR(255),
  PRIMARY KEY(`id`)
);

-- Create table `news`
CREATE TABLE IF NOT EXISTS `news` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `category_id` INT UNSIGNED NOT NULL,
  `title` VARCHAR(255),
  `view` INT UNSIGNED,
  `is_active` TINYINT(1),
  `content` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`category_id`) REFERENCES category(id)
);

-- Create table `comment`
CREATE TABLE IF NOT EXISTS `comment` (
    `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `target_table` VARCHAR(20),
  `target_id` INT UNSIGNED,
  `user_id` INT UNSIGNED NOT NULL,
  `comment` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`user_id`) REFERENCES user(id)
);

-- Create table `follow`
CREATE TABLE IF NOT EXISTS `follow` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `from_user_id` INT UNSIGNED NOT NULL,
  `to_user_id` INT UNSIGNED,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`from_user_id`) REFERENCES user(id),
  FOREIGN KEY (`to_user_id`) REFERENCES user(id)
);

-- Create table `blog`
CREATE TABLE IF NOT EXISTS `blog` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `category_id` INT UNSIGNED NOT NULL,
  `user_id` INT UNSIGNED NOT NULL,
  `title` VARCHAR(255),
  `view` INT UNSIGNED,
  `is_active` TINYINT(1),
  `content` TEXT,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY(`id`),
  FOREIGN KEY (`category_id`) REFERENCES category(`id`),
  FOREIGN KEY (`user_id`) REFERENCES user(`id`)
);

-- Import database
use train_mysql;
source /only_data.sql;