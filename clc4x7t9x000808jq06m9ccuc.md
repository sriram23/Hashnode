# The RUST Language

Hello World!

RUST LANG

**Rust** is a system programming language with the goals *of Safety, Speed* and *Concurrency.* Rust is good at embedding with other languages. It has several compile-time safety checks that eliminate the data *races.*

#### How to install it?

For ***Linux*** and ***Mac***, open the terminal and enter the following command.

> $ curl [https://sh.rustup.rs](https://sh.rustup.rs) -sSf | sh

For **Windows**, download and install [this file](https://win.rustup.rs/).

To verify whether Rust is installed, enter the command

> $ rustc --version

### Cargo

Cargo is Rust’s build system and package manager. It does three things

* Building the code
    
* Downloading the Dependencies and Libraries
    
* Building the Libraries
    

We can check whether the cargo is installed by typing

> $ cargo — version

### Hello World — Rust Program

Now let us write a Rust program that prints the text “Hello World!”

* First, move to the destination where to write the program. For example /home/User/Documents/RUST.
    
* Now open the terminal and type
    

> cargo new hello\_world --bin

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066090939/S-kvizQ-y.png align="left")

Creating new Cargo

When we list the files in *hello\_world* it will have *Cargo.toml* and *src* directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066092339/TOhuI-A-C6.png align="left")

In the *src directory,* we have the *main.rs*, in which we write the code. In *Cargo.toml*, we give the dependencies.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066093616/OSiz0Q-Jn.png align="left")

Cargo.toml

* Let’s write the code for the “Hello World” program. For that, we need to open the *main.rs* file in an editor. I use *nano* editor, which is accessible in the Linux terminal. Write the code and save the file.
    

> $ nano src/main.rs

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066095103/eOJb70wLE.png align="left")

Rust code for Hello World!

Here, *fn* keyword denoted the function declaration and *main()* is the main function.

The *println!()* method is used to print the values to the output console.

Now, let us build and run the code. The command used to build the code is

> $ cargo build

The command to run the code is

> $ cargo run

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066097543/FSVjCYLBh.png align="left")

Output of Hello World program

Now, we have installed Rust in our system and executed a simple *Hello World* program in Rust. Since this is a very simple program and need no dependencies, we left the *Cargo.toml* unchanged.

Looking forward for your valuable feedbacks and suggestions.

Thank you!!