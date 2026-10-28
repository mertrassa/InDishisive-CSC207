# InDishisive

> *Indecisive, but with **Dish** in the middle.*

InDishisive is a desktop recipe assistant for people who can't decide what to cook. Tell it what's in your kitchen, what you can't eat, or what cuisine you're in the mood for, and it suggests meals for you. Recipes come from [TheMealDB](https://www.themealdb.com/).

It was built as the team project for **CSC207 (Software Design)** at the University of Toronto, following Clean Architecture.

## Features

- **Inventory:** search TheMealDB's ingredient list and keep track of what you have at home.
- **Generate recipes:** get meals that use your inventory, or search by specific ingredients.
- **Filter by cuisine:** narrow the generated recipes down to one cuisine.
- **Random recipe:** for when you really can't decide.
- **Recipe details:** see ingredients and instructions, and open the cooking video on YouTube.
- **Missing ingredients:** compare a recipe against your inventory and export a shopping list.
- **Favorites:** save recipes you like and come back to them later.
- **Dietary restrictions:** add ingredients you avoid, and generated recipes that contain them are left out.
- **Your own recipes:** write, view and delete your own recipes.

## Getting started

### Requirements

- Java 17 or newer
- Maven
- An internet connection (recipes are fetched from TheMealDB)

### Run

1. Clone the repository:

   ```bash
   git clone https://github.com/mertrassa/InDishisive-CSC207.git
   cd InDishisive-CSC207
   ```

2. Open the project in IntelliJ IDEA (or any IDE with Maven support) and let it import the dependencies from `pom.xml`.
3. Run `src/main/java/app/Main.java`.

### Saved data

The app saves your data as files in the directory you run it from:

| File | Contents |
| --- | --- |
| `inventory.json` | Your ingredient inventory |
| `favorites.json` | Favorite recipes |
| `restrictions.json` | Dietary restrictions |
| `user_recipes.tsv` | Recipes you wrote |
| `shopping_list.txt` | Exported missing ingredients |

## Project structure

The code follows Clean Architecture, with one package per layer under `src/main/java`:

| Package | Layer |
| --- | --- |
| `entity` | Core data: `Recipe`, `Ingredient`, `Inventory`, `UserRecipe` |
| `logic` | Use cases (interactors, input/output boundaries and data) |
| `adapters` | Controllers, presenters and view models |
| `databases` | Data access objects for local files and TheMealDB API gateways |
| `view`, `window` | Swing user interface |
| `app` | `AppBuilder` wires everything together; `Main` launches the app |

Each feature has its own sub-package in every layer. For example, filtering by cuisine is spread across `logic/generate_recipe/filter_by_cuisine`, `adapters/generate_recipe/filter_by_cuisine` and `databases/generate_recipe/MealDbCuisineDataAccessObject`.

Tests are in `src/test`.

## Built with

- Java Swing
- [OkHttp](https://square.github.io/okhttp/) for HTTP requests
- [org.json](https://github.com/stleary/JSON-java) for parsing API responses
- JUnit 5

## Team

Forked from the team repository [UniversalSaver/InDishicive](https://github.com/UniversalSaver/InDishicive). Thanks to everyone who contributed there.
