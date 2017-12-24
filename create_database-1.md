###1. Tạo database
```
CREATE SCHEMA IF NOT EXISTS `train-mysql` DEFAULT CHARACTER SET utf8 ;
USE `train-mysql` ;
```
# Table `train-mysql`.`user` 
```
CREATE TABLE IF NOT EXISTS `user` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `full_name` VARCHAR(255) NOT NULL,
  `email` VARCHAR(255) NOT NULL UNIQUE,
  `rank` TINYINT(4) NOT NULL,
  `is_active` TINYINT(1) NULL,
  `create_at` TIMESTAMP NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB;
```
#Table `train-mysql`.`comment`
```
CREATE TABLE IF NOT EXISTS `comment` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `target_table` VARCHAR(20) NOT NULL,
  `target_id` INT(11) NOT NULL,
  `user_id` INT(11) NOT NULL,
  `comment` TEXT NOT NULL,
  `create_at` TIMESTAMP NULL,
  `update_at` TIMESTAMP NULL,
  PRIMARY KEY (`id`),
  INDEX `fk_comment_user1_idx` (`user_id` ASC),
  CONSTRAINT `fk_comment_user1`
    FOREIGN KEY (`user_id`)
    REFERENCES `user` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
#Table `train-mysql`.`follow`
```
CREATE TABLE IF NOT EXISTS `follow` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `from_user_id` INT(11) NOT NULL,
  `to_user_id` INT(11) NOT NULL,
  `create_at` TIMESTAMP NULL,
  PRIMARY KEY (`id`),
  INDEX `fk_follow_user1_idx` (`from_user_id` ASC),
  INDEX `fk_follow_user2_idx` (`to_user_id` ASC),
  CONSTRAINT `fk_follow_user1`
    FOREIGN KEY (`from_user_id`)
    REFERENCES `user` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_follow_user2`
    FOREIGN KEY (`to_user_id`)
    REFERENCES `user` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
#Table `train-mysql`.`category`
```
CREATE TABLE IF NOT EXISTS `category` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `title` VARCHAR(255) NOT NULL,
  `description` VARCHAR(255) NOT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB;
```
#Table `train-mysql`.`blog`
```
CREATE TABLE IF NOT EXISTS `blog` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `category_id` INT(11) NOT NULL,
  `user_id` INT(11) NOT NULL,
  `title` VARCHAR(255) NOT NULL,
  `view` INT(11) NOT NULL,
  `is_active` TINYINT(1) NULL,
  `content` TEXT NULL,
  `create_at` TIMESTAMP NULL,
  `update_at` TIMESTAMP NULL,
  INDEX `fk_blog_user_idx` (`user_id` ASC),
  INDEX `fk_blog_category1_idx` (`category_id` ASC),
  PRIMARY KEY (`id`),
  CONSTRAINT `fk_blog_user`
    FOREIGN KEY (`user_id`)
    REFERENCES `user` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_blog_category1`
    FOREIGN KEY (`category_id`)
    REFERENCES `category` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION)
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8
COLLATE = utf8_unicode_ci;
```

#Table `train-mysql`.`news`
```
CREATE TABLE IF NOT EXISTS `news` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `category_id` INT(11) NOT NULL,
  `title` VARCHAR(255) NOT NULL,
  `view` INT(11) NOT NULL,
  `is_active` TINYINT(1) NULL,
  `content` TEXT NULL,
  `create_at` TIMESTAMP NULL,
  `update_at` TIMESTAMP NULL,
  INDEX `fk_blog_category1_idx` (`category_id` ASC),
  PRIMARY KEY (`id`),
  CONSTRAINT `fk_blog_category10`
    FOREIGN KEY (`category_id`)
    REFERENCES `category` (`id`)
    ON DELETE NO CASCADE 
    ON UPDATE NO ACTION)
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8
COLLATE = utf8_unicode_ci;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;

```