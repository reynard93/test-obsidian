## hashmaps
create from two vec calling iter and using zip to join them tgr
	call collect to turn it into a hashmap
for owned_values, values are moved into the hashmap
	otherwise values are copied
use insert to overwrite/write 

## generics
to define a generic impl
impl<T> Point<T> {  
    fn x(&self) -> &T {  
        &self.x  
    }  
}

performance does not take a hit when using generics, during compile time it is 'monomorphized'

traits define shared behavior in an abstract way
example is to implement a summary method on two different types of source "tweet", or "news article"
they are similar to interfaces in other languages

traits are defined using the trait keyword
you can implement the trait for a struct
	although most traits end with ; you can define actual functions instead, this will allow you to provide 'default implementation' so therefore in yr struct instead of defining a custom implementation we can specify an empty impl block
	`
		impl Summary for NewsArticle {}
	// where the trait comes before the struct
	`
impl Summary for NewsArticle
we can implement **only** if either trait or the type is local to our crate, to adhere to coherence

pub fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}
this is a syntax sugar for a longer form which is called trait bound

trait bound syntax affords us more complexity for example if we want two items to have the same type
pub fn notify<T: Summary>(item1: &T, item2: &T) {

The generic type T specified as the type of the item1 and item2 parameters constrains the function such that the concrete type of the value passed as an argument for item1 and item2 must be the same.
note: for different types okay, but for same type we need to constrain it

you can also specify multiple traitbounds with the '+' syntax
pub fn notify(item: &(impl Summary + Display))

this syntax is also valid with **trait bounds** on generic types
pub fn notify<T: Summary + Display>(item1: &T, item2: &T) {
The generic type T specified as the type of the item1 and item2 parameters constrains the function such that the concrete type of the value passed as an argument for item1 and item2 must be the same.

we can also define cleaner trait bounds with `where` clause
So instead of writing this:

fn some_function<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) -> i32 {

we can use a where clause, like this:

fn some_function<T, U>(t: &T, u: &U) -> i32
    where T: Display + Clone,
          U: Clone + Debug
{

This function’s signature is less cluttered: the function name, parameter list, and return type are close together, similar to a function without lots of trait bounds.

we can use `impl Trait` in the return position to return a value of some type that implements a trait, here Tweet impl Summary
fn returns_summary() -> impl Summary {
	Tweet {...}
}
this ability is especially useful for closures and iterators, this only works if you are returning a single type
(you can just specify the type returned impl a certain Trait, instead of a list of types/very long type)
single type: in the above example if were to return a NewsArticle given if else then it woulndt work

impl<T: Display + PartialOrd> Pair<T> {  
    fn cmp_display(&self) {  
        if self.x >= self.y {  
            println!("The largest member is x = {}", self.x);  
        } else {  
            println!("The largest member is y = {}", self.y);  
        }  
    }  
}
this trait bound makes the cmp_display method implemented conditionally; for the Pair struct -only if its inner type implements both trait

traits and trait bounds let us write code that uses generic params but also specify we want the
 generic type to have particular behavior

lifetimes are another kind of generic, they ensure that references are valid as long as we need them to do