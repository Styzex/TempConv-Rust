# TempConv
Its a simple Celsius to Fahrenheit and vice versa converter made using Rust
There are no dependecies except of the std library.

Preview:
![preview](https://github.com/user-attachments/assets/0d020efc-a583-4cbd-8ff1-49f173a91101)

Code:
```
use std::io;

fn input_handling(temp: &str) {
    let mut opt = "CtoF";
    let result;
    let mut temp_input = String::new();

    if temp.trim() == "1" || temp.trim() == "1." || temp.trim() == "C" {
        println!("You chose to convert °C to °F");
        opt = "CtoF"
    } else if temp.trim() == "2" || temp.trim() == "2." || temp.trim() == "F" {
        println!("You chose to convert °F to °C");
        opt = "FtoC"
    } else {
        println!("Nothing was selected using the default option Celsius to Fahrenheit");
    }

    if opt == "CtoF" {
        println!("What temperature do you want to convert?");
        io::stdin()
            .read_line(&mut temp_input)
            .expect("Failed to read line");
        result = temp_input.trim().parse::<i32>().unwrap() * (9/5) + 32; // °F = °C * 9/5 + 32
        println!("{}°C is equal to {}°F", temp_input.trim().parse::<i32>().unwrap(), result);
    } else if opt == "FtoC" {
        println!("What temperature do you want to convert?");
        io::stdin()
            .read_line(&mut temp_input)
            .expect("Failed to read line");
        result = (temp_input.trim().parse::<i32>().unwrap() - 32) / (9/5); // °C = (°F - 32) ÷ (9/5)
        println!("{}°F is equal to {}°C", temp_input.trim().parse::<i32>().unwrap(), result);
    } else {
        println!("Mutable opt wasnt initialized");
    }
}

fn main() {
    println!("");
    println!("Pick a temperature unit to convert from:");
    println!("1. Celsius to Fahrenheit");
    println!("2. Fahrenheit to Celsius");

    let mut input = String::new();

    io::stdin()
        .read_line(&mut input)
        .expect("Failed to read line");

    input_handling(&input);
}
```
