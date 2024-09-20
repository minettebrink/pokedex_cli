# Pokedex

This project is part of [boot.dev](https://www.boot.dev/). The assignment was _Build a REPL pokedex on the command line in Go_. 

It's a Pokedex-like REPL in Go. It uses the PokeAPI to fetch data about different Pokemons. You can move the map, search for, catch, and inspect different Pokemons.

The goal of this project is to learn Go and to:
- become comfortable with JSON APIs
- make network requests
- implement caching

## How to run it
- Make sure you have [Go](https://go.dev/) installed
- Clone the git repo
```
git clone https://github.com/minettebrink/pokedex_cli.git
cd pokedex_cli
```
- Build from source with:
```
go mod tidy 
go build 
```
- Start the application
```
./pokedex_cli
```
### How to use it 
Type help to get further instructions
```
Pokedex > help 
```
After typing help, you will get the following output.
```
Welcome to the Pokedex!
Usage:

mapb: Get the previous page of locations
pokedex: See all the pokemon you've caught
exit: Exit the Pokedex
help: Displays a help message
catch <pokemon_name>: Attempt to catch a pokemon
inspect <pokemon_name>: View details about a caught Pokemon
explore <location_name>: Explore a location
map: Get the next page of locations

Pokedex >
```
Type `map` to see what locations you can go, with `mapb` can you go back a page.
```
Pokedex > map
canalave-city-area
eterna-city-area
pastoria-city-area
sunyshore-city-area
sinnoh-pokemon-league-area
...
```

Use `explore` to see what Pokemons are in that location.
```
Pokedex > explore canalave-city-area
Exploring canalave-city-area...
Found Pokemon: 
 - tentacool
 - tentacruel
 - staryu
 - magikarp
 - gyarados
 ...
```
Continue by catching Pokemons and creating an impressive Pokedex!

## Project workflow 
I started with creating the REPL, implemented in [repl.go](repl.go), along with basic commands: 
- `help`, [command_help.go](command_help.go), 
- `exit`, [command_exit.go](command_exit.go).

Next, I integrated the [PokeAPI](internal/pokeapi/) to enable fetching Pokémon data. 

To enhance the user experience, I implemented caching in [pokecache directory](internal/pokecache/). This allows for certain data to be stored rather than constantly requested.

After this, I added various commands to be able to move and catch Pokemons:
- The command `map`, implemented in[command_map.go](command_map.go), displays 20 locations within the Pokémon world.
- The command `mapb`, implemented in[command_mapb.go](command_mapb.go), shows the 20 previous locations for easier navigation.
- For exploring different locations: `explore <location>`, implemented in [command_explore.go](command_explore.go).
- To be able to catch Pokémons: `catch <pokemon_name>`, implemented in [command_catch.go](command_catch.go)
- After catching a Pokémon, you can inspect it using the command `inspect <pokemon_name>`, implemented in  [command_inspect.go](command_inspect.go).
- Finally, the `pokedex` command lets you view all the Pokémon you've caught, implemented in [command_pokedex.go](command_pokedex.go).

