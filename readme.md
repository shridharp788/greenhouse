**This is demo project for Greenhouse Presentation for laravel and vuejs skills **

The steps how I have created this project are as below 

This is CRUD Project which demonstrates usage of vuejs and laravel api 

  1. User signup form is presented and on submit data is saved to sqlite and a tabular list is 
  updated below the form in descedning order 

  2. On first load , existing users are listed in ascending order 

  3. On every save of data, saved flash message is returned 

  4. Created laravel skeleton project 

  5. Npm installed vue js , bootstrapjs , jqueryjs

  6. Created a form to take inputs email , usename and gender

  7. Created greenhouse.sqlite database in laravel root directory 

  8. Configured laravel to use sqlite database 

  9. Created controller greenhouse using php artisan make:controller

  10. Created vuejs component dashboard and added in laravel-vue/resources/assets/js/components/DashboardComponent.vue

  11. Updated app.js laravel-vue/resources/assets/js/app.js

  12. Added methods in Greenhousecontroller to return users from sqlite database 

**How to run this project ?**

In Single terminal run one by one

1. composer install --no-dev 

2. php artisan serve 

In other terminal also run one by one 
1. npm install 
2. npm run watch 



