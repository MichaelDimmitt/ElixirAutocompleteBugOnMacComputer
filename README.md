# ElixirAutocompleteBugOnMacComputer

The sorting done by IEx.Autocomplete does not actually do anything! At the end of the day it either defers to either erlangs autocomplete, or the operating system itself.
(Disclaimer: unless I am missing something!)

Also the elixir output for autocomplete has the same bug that mac operating systems have in that they do a lexographical sort. Atleast on a mac operating system!
(The perpose of this project is to prove the bug!)

The bug is that when pattern matching to the same function with different airity, numbers past 10 but below 20 will show after arity of 1 and before arity of 2 but not at the end of the list like you would expect in a numerical sort. This is due to how lexographical sorts work, and from what I can gather in a quick research spike, is used by the operating system over a name + numerical for performance reasons. This same problem exists with folder names in the mac operating system. There is and LC_... config variable that might fix this issue for folders in certain operating systems. Still researching an LC_... fix.

The bug is visible in the screenshot below where the function having the same name is out of order due to functions having an arity greater than 10.
(Disclaimer, this be considered pointless because who writes functions with an arity greater than 10 ?)

Mostly this is just for fun discussion!

## Installation
Do standard install things like download erlang and elixir and mix as needed.

To run the project use:
`iex -S mix;`

In the shell that opens type:
1. "ElixirA"
2. <tab>
3. <tab>
4. he
5. <tab>

Now you should see your module of the project and the functions for hello.
Basically all the commands described and the output are shown in this screenshot:



<!-- 

## Installation

The below stuff is always wrong for a person making an elixir project for the first time. That is about the publish phase of a project...

This installation sections should really include solely.
Get started by running iex -S mix 

your project name is the module put a capital letter of your project name and hit tab to autocomplete to the full module name.

put a . and hit tab a few more times to get autocomplete to expose the hello function.

type he and then tab to autocomplete.

and hit enter to see the function return :world.

^ or atleast they should just put a link to if you are writing the library for the first time go here to this getting started link for mix.

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `elixir_autocomplete_bug_on_mac_computer` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:elixir_autocomplete_bug_on_mac_computer, "~> 0.1.0"}
  ]
end
```

-->

Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at <https://hexdocs.pm/elixir_autocomplete_bug_on_mac_computer>.

## Acknowledgement:
Shout out to github.com/murjax for finding the bug when I figured out how to get the autocomplete to sort by arity.
