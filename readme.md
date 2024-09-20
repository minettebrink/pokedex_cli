# Pokedex

This project is a part of [boot.dev](https//boot.dev). The assignment was _Build a REPL pokedex on the command line in Go_. 

So, it is a Pokedex-like REPL in Go. It uses the PokeAPI to fetch data about different Pokemons. Then, in the REPL, you can, for example, search, catch or inspect different Pokemons. 


The goal of this project: 
- learn how to use JSON 
- make network requests
- implement caching

## Abit about the code
- Started by creating a REPL, [repl.go](repl.go) and help, [command_help.go](command_help.go) and exit, [command_exit.go](command_exit.go) commands.  

- Connect to the PokeAPI, [pokeapi](internal/pokeapi/)

- Implemented caching [pokecache](interal/pokecache) to make moving around smoother. It made it possible to store some data instead of always requesting it. 

## Different commands
- The the PokeAPI was added. The [command_map.go](command_map.go) displays 20 different locations in the Pokemon world and [command_mapb.go](command_mapb.go) displays the 20 previous locations.

- You may want to be able to explore different locations by the [command_explore.go](command_explore.go).

- When you need to be able to catch a Pokemon, [command_catch.go](command_catch.go) enables you to catch them.

- When you have caught a Pokemon, you can inspect it [command_inspect.go](command_inspect.go).

- The Pokedex command lets you see all the Pokemons that you have caught, [command_pokedex.go](command_pokedex.go).




## How to run it 
- Install [Go](https://go.dev/) 
- Clone the git repo
```
git clone https://github.com/minettebrink/pokedex_cli.git
cd pokedex_cli
```

- Build the hack

```
go mod tidy 
go build 
```

## How to use it 
Type help when you see Pokedex to get further instructions

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