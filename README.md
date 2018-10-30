# js-precompiles-
js-预编译过程

   预编译 四部曲：   
         1：创建AO对象  
         2：找形参和变量声明，将变量和形参名作为AO对象属性名，值为undefined  
         3：将实参值和形参统一 
         4：在函数体里面找函数声明，值赋予函数体
         
         
           function test(a){
             console.log(a)   // function a(){};
             var a=123;
             console.log(a)  //123
             function a(){};
             var a=256;
             console.log(a) //256
             var b=function(){};
             console.log(b)  //function(){};
          }
             test(2)


  
         function test(a){
             console.log(a)    // function a(){};
             var b=200000;
             var a=123;
             console.log(b);   //200000
             console.log(a)    //123
             function a(){};
             var a=256;
             console.log(a)     //256
             var b=function(){};
              console.log(b)     //function(){};
             function b(){};
              console.log(b)     //function(){};
            }
        test(2)



             function test(){
                 return foo;
                 foo=123;
                 function foo(){};
                 var foo=900;
             }
           console.log(test())     //   function foo(){};



              function test(){
                    return foo;
                    foo=123;
                    var foo=900;
                }
              console.log(test())     //   undefined



                function test(){
                    foo=123;
                    function foo(){}
                    var foo=900;   
                    return foo    //只要是上面被赋过值，下面就直接输出
                }
               console.log(test())     //   900



