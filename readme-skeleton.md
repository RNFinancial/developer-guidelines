# Repository Name
*optional tagline*

- [1.0 Objective](#10-objective)
- [2.0 Installation](#20-installation)
- [3.0 Usage](#30-usage)
- [4.0 First Module](#40-first-module)
  - [4.1 Module Class](#41-module-class)
  - [4.2 Module Functions](#42-module-functions)
  - [4.3 Module Database](#43-module-database)

## 1.0 Objective

Short description of the project here.

## 2.0 Installation

How to install the code.

```sh
$ git clone git@github.com:RNFinancial/developer-guidelines
```

## 3.0 Usage

How to use the code. Examples are very helpful here.

```python
import math

math.random()
```

## 4.0 First Module

A short description of what the module does, this one tracks pizza orders.

### 4.1 Module Class

Class `pizza` that bakes and delivers a pizza.

Properties:

| Property | Type | Description |
|:---------|:-----|:------------|
| `r`      | `int` | Pizza's size. |
| `slices` | `int` | Number of slices. |
| `crust`  | `str` | The type of crust on the pizza. |
| `toppings` | `list` | List of toppings on the pizza. |
| `baked`  | `bool` | Whether the pizza is baked. |

Methods:

| Method | Parameters | Return | Description |
|:-------|:-----------|:-------|:------------|
| `__init__` | `r` - `int` with pizza size. <br/><br/> `crust` - `str` with pizza size. <br/><br/> |  | Creates a new pizza. |
| `add_topping` | `*args` - `str` with new topping to add. | `list` of current toppings. | Adds a topping to the pizza. |
| `bake` | `time` - `int` with the duration to bake. |  | Sets the Pizza's `baked` property` `true.` |
| `deliver` | `address` - `str` with the address to deliver to. | `float` with cash received. | Delivers the pizza to the specified address if it has been baked. |

Usage:

```python
import pizza

p = pizza.pizza(r=12, crust='thin')
p.add_topping('cheese', 'pepperoni', 'onions', 'olives', 'olives') # Add extra olives.
p.bake(15)
p.deliver('130 Adelaide St W.')
```

### 4.2 Module Functions

A small library that manages pizza orders.

| Function | Parameters | Return | Description |
|:---------|:-----------|:-------|:------------|
| `order_pizza` | `address` - `str` with user's address. <br/><br/> `size` - `str` with pizza size. <br/><br/> `toppings` - `list` of toppings. <br/><br/> `crust` - `str` with crust type. Defaults to `thin`. | `bool` if pizza was successfully ordered. | Takes the users order and address and orders a pizza. |

Usage:

```python
import pizza

ordered = pizza.order_pizza('130 Adelaide St W.', 10, ['cheese', 'pepperoni', 'onions', 'olives', 'olives'])
print(ordered)
```

### 4.3 Module Database

The `pizza` database uses MongoDB to store the different types of pizzas and their toppings. The dbname is `pizza` and collection is `toppings`.

| Field | Type | Index | Description |
|:------|:-----|:------|:------------|
| `name` | `str` | ✓ | Name for the pizza. |
| `sku`  | `int` |   | Internal SKU for the pizza type. |
| `toppings` | `array` |  | List of toppings for making the pizza. |

Example Query:

```python
from pymongo import MongoClient

client = MongoClient()
pizza = client['pizza']['toppings'].find_one({'name': 'Hawaiian'})

for topping in pizza['toppings']:
  print(topping)
```
