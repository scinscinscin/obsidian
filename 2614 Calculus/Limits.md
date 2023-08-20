 - Describes the behavior of a function in the vicinity of a number as opposed to the value of the function in a given number
	 - approximate value
	 - the definition of the limit refers to refers to the two sided limit since there are two directions to approach the number, left and right
 - L is the limit of f(x) as x approaches a

**One sided limit**
 - when approach of x to a is confined on one side, it is indicated by writing x->a+ or x->a- instead of x->a
	 - plus sign - approach from the right
	 - minus sign - approach from the left side

**Theorems**
 - the limit of a function is unique
 - the limit of f at a exists if the limit exists from the left and right side and they are equal
 - the limit of a constant c is c
 - the limit of x^n = a^n
 - limit can be distributed between addition / subtraction / multiplication and division
	 - `lim (f(x) / g(x))` is `lim(f(x)) / lim(g(x))` if g(x) != 0
 - limit can be distributed among powers / exponents and roots

**Infinite limits**
 - if f(x) approaches a definite number L as x becomes large without bound, it is written as `lim x->infinity f(x) = L`
	 - the line `y=L` is called the **horizontal asymptote** of the curve, f(x) approaches this line but never touches it
 - if f(x) becomes arbitrarily large as x approaches a number a, it is written as `lim x->a f(x) = infinity`
 - `lim x->0 c/x = infinity` where c is a constant
 - `lim x->infinity c/x^n = 0` where c is a constant
	 - the denominator becomes exponentially larger, so the quotient becomes exponentially smaller, approaching 0

**Continuity**
- a number is continuous on an interval if it is continuous at every number in that interval
- f(x) is continuous at the number a if
	- `f(a)` is defined
	- `lim x->a f(a)` exists and it is equals to `f(a)`
- **theorems**
	- the sum / difference / and product of continuous functions is also continuous
	- the quotient of two continuous functions is also continuous except at those numbers where the denominator equals zero
	- the polynomial function is continuous at any real number
- types of discontinuity
	- `f(a)` is not defined - missing hole
	- `f(a) != lim x->a f(x)` - the limit is not equal to evaluation
		- appears as a solid dot over a hollow dot in the line of the function
	- `lim x->a f(x)` does not exist
		- the limit taken from the left and right is not equal
	- neither is `f(a)` defined nor does the limit exist

