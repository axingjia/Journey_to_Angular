# Journey_to_Angular

# To AngularJS
* Link: angularjs.org
* builtwith.angularjs.org
* plnkr.co is built with angularjs
* Javascript pattern: abstraction, build module, avoid global variables

###### $http service

        $scope.user=$http.get('/user/1828');

* $http is asynchronous,
* $http returns a promise, a promise to deliver a value in the future

        var promise=$http.get('/user/1818');
        promise.then(function(response){
            $scope.user=response.data;
        });

        or

        $http.get('...').
            then(function(response){
                $scope.user=response.data;
            },function(reason){
                $scope.error="could not fetch the user";
            });

* * *

* github API
* angular module

        var app=angular.module("moduleName",[]);
        app.controller('nameOfController',function($scope,$http){

        });

* Always use IFFE to avoid global variable

        app.controller("MainController"),['$scope','$http',function($scope,$http){

            }])

* This is for minifying the code

        <input type="search" ng-model="username"/>
        <input type="submit" value="Search" ng-click="search()" />

        $scope.search=function(username){
            $http.get("...").then(function(response){

            })
        }

* www.gravatar.com/avatar/{{user.gravatar_id}}
* if one input is required, you can't use ng-click, use ng-submit on the form tag instaed

        {{count | number: 1}}
        //one digit after the number

* this is a filter. Ex: json, date, filter, limitTo, lowercase, uppercase, orderBy:"+-name"
* order by with positive sign means ascending order
* ng-show and ng-hide

###### ng-include directive

    userdetail.html

    <div ng-include="''"></div> //use single quote inside a double quote so it doesn't find it in the scope and interpret it as a string

* * *

* $timeout and $interval service
        var countdownInterval=null;
        var startCountdown=function(){
            countdownInterval=$interval(decrement,1000,5); // a service that you can invoke
        }
        starCountdown();

        //inside search function
        function(){
            if(countdownInterval){
                $interval.cancel(countdownInterval);
            }
        }


* $log service

        $log.info('searching for');

* $location and $anchorScroll service

        $location.hash("userDetail");
        $anchorScroll();

* custom service

        var github=function(){
            return{
                ...
            }
        }
        var module=angular.module("...");
        module.factory('github',github);

### Routing
* angular-route.js module
* $routeProvider

        //inside index.html
        <div ng-view></div>


        var app=angular.module('githubViewer',['ngRoute']);
        app.config(function($routeProvider){
            $routeProvider
                .when("/main",{
                        templateUrl:"mainhtml",
                        controller:"MainController"
                    })
                .when('/user/:username',{
                        templateUrl:'user.html',
                        controller:"UserController"
                    })
                .otherwise({redirectTo:"/main"});
        });

        //inside a userController.js

        var ..Controller=function($scope,$routeParams){ //include $routeParams

            $scope.username=$routeParams.username;
        }
        //inside MainController

        $location.path('/user'+username)

# Angular 2+
* www.joeeames.me
* johnpapa.net

## Angular CLI
* node 8.x or higher
* npm 5.x or higher
* npm i @angular/cli -g
* cli.angular.io
* angular.io
* ng new my-app
ng new my-app --skip-install //generate without running npm install
