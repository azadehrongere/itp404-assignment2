<script> 

var string = {
  pluralize: function(word) {
    if (word.substr(-1)== 'y'){
      word = word.substr(0, word.length-1);
      word+='ies';
    }
    // word.substr keeps all characters in the string from 
    // index 0 to length - 1 
    else {
      word += 's';
    }
    // word+= simply adds s to the end of the string 
    console.log(word);
  }
  
};


string.pluralize('cat');
string.pluralize('baby');

//////

function Book ({title, quantity, price}){
  this.title = title; 
  this.quantity = quantity; 
  this.price = price;
}

function ShoppingCart ([Book1, Book2]){
   this.items = [];
   this.items.push(Book1);
   this.items.push(Book2);
   // pass in two book objects for sake of problem
   // .push function adds object to end of array
}

ShoppingCart.prototype.add = function(book){
  this.items.push(book);
  // creating shopping cart add function 
  // shoppingcart add is just pushing an object into an array
}

ShoppingCart.prototype.getTotal = function(){
  var total = this.items.reduce(function(accumulator, book){
    return accumulator + book.getSubtotal();
    // reduce function goes through array of book objects 
    // accumulator adds up book totals
  }, 0);
   return total;
}



Book.prototype.getSubtotal = function() {
    return this.quantity * this.price;
    // get subtotal adds quantity and price of books
}


var book1 = new Book({ title: 'Object Oriented JavaScript', quantity: 1, price: 10 });
var book2 = new Book({ title: 'JavaScript Web Applications', quantity: 2, price: 15 });
var book3 = new Book({ title: 'PHP Object Oriented Solutions', quantity: 1, price: 20 });
var book4 = new Book({ title: 'Head First Java', quantity: 5, price: 20 });


var cart = new ShoppingCart([book1, book2]);
cart.add(book3);
cart.add(book4);
console.log(cart);
var subtotal = cart.getTotal();
console.log(subtotal); 

// shooping cart function takes in 2 book objects and adds them to shopping cart array
// cart.add adds objects to shopping cart array 


/////////////


Array.prototype.map2 = function(callbackFunction){
  var array = [];
  for (var i=0; i<this.length; i++){
    array.push(callbackFunction(this[i]));
  }
 return array;
}



var numbers = [1, 2, 3, 4, 5];
var numbersDoubled = numbers.map2(function(number) {
  return number * 2;
});

console.log(numbersDoubled); 




</script>
