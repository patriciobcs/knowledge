type:: [[Software]], [[Testing]]
description:: A bit-precise model checker for Rust.

- ## Setup   
    
  On the project to test, execute:  
  ``` sh
  		  cargo install --locked kani-verifier
  		  cargo-kani setup
  ```
    
  > Check the official [Installation Guide](https://model-checking.github.io/kani/install-guide.html) for more details
- ## Structure  
    
  The basic structure of a Kani test:  
  ``` rust
  		  #[cfg(kani)] 
  		  #[kani::proof] 
  		  fn test_name() { 
  		  	...
  		  }
  ```
- ## Visualize
	- ### Code Coverage  
	    
	  `Green lines:`  totally covered  
	  `Red lines:`  not covered  
	    
	  ``` sh
	  			  cargo kani --visualize --harness <test-name>
	  ```
	- #### Trace  
	    
	  ``` sh
	  			  cargo kani --visualize
	  ```
	- ## Harness
		- #### Test any value at once  
		    
		  Assign `kani::any()`  to the values on the tests  
		    
		  ``` rust
		  				  let x: u32 = kani::any();
		  ```
		    
		  This will create a similar output as a fuzzing tool (`proptest`) but with a totally different execution and more coverage. It will even analyze unsafe code, memory leaks, etc.
		- #### Explicit the conditions  
		    
		  Use `assert` to explicit the execution conditions  
		    
		  ``` rust
		  				  assert!(x < y);
		  ```
		- #### Explicit the assumptions  
		    
		  Use `assume` to explicit the scope of the values of the variables.   
		    
		  ``` rust
		  				  kani::assume(x < y);
		  ```
		    
		  This could reduce the code coverage, always double check that the assumptions are correct.