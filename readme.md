**This is demo project for Greenhouse Presentation for laravel and vuejs skills **

The steps how I have created this project are as below 

This is CRUD Project which demonstrates usage of vuejs and laravel api 

  User signup form is presented and on submit data is saved to sqlite and a tabular list is 
  updated below the form in descedning order 

  On first load , existing users are listed in ascending order 

  On every save of data, saved flash message is returned 

  Created laravel skeleton project 

  Npm installed vue js , bootstrapjs , jqueryjs

  Created a form to take inputs email , usename and gender

  Created greenhouse.sqlite database in laravel root directory 

  Configured laravel to use sqlite database 

  Created controller greenhouse using php artisan make:controller

  Created vuejs component dashboard and added in laravel-vue/resources/assets/js/components/DashboardComponent.vue

  Updated app.js laravel-vue/resources/assets/js/app.js

  Added methods in Greenhousecontroller to return users from sqlite database 

**How to run this project ?**

In Single terminal run one by one

1. composer install --no-dev 

2. php artisan serve 

In other terminal also run one by one 
1. npm install 
2. npm run watch 



