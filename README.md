# ElixirAutocompleteBugOnMacComputer
Elixirs iEX autocomplete output has a bug! 

The same bug that mac operating systems have with file names in that they do a lexicographical sort.  
(The purpose of this project is to prove the bug!)

<!--
The sorting done by IEx.Autocomplete does not actually do anything!  
At the end of the day it either defers to either erlang's autocomplete, or the operating system itself.  
(Disclaimer: unless I am missing something!)

The bug is visible when functions have the same name with different arity, numbers past 10 but below 20 will show after arity of 1 and before arity of 2 but not at the end of the list like you would expect in a numerical sort.
-->

<!--
This is due to how lexicographical sorts work, and from what I can gather in a quick research spike, is used by the operating system over a name + numerical for performance reasons. This same problem exists with folder names in the mac operating system. There is and LC_COLLATE config variable that might fix this issue for folders in certain operating systems. Still researching an LC_COLLATE fix.
-->
The bug is visible below in the Installation section screenshot. In the screenshot the function having the same name is out of order due to functions having an arity greater than 10.  
(Disclaimer, this bug may be considered pointless because who writes functions with an arity greater than 10 ?)  

Mostly this is just for fun discussion!

## Installation
Do standard install things like download erlang and elixir and mix as needed.

To run the project use:
`iex -S mix;`

In the shell that opens type:  
`iex> ElixirAutocompleteBugOnMacComputer.hello<tab>`

Now you should see your module of the project and the functions for hello.
Basically all the commands described and the output are shown in this screenshot:

![example](/terminal_example.png)

<!--

## Installation

The below stuff is always wrong for a person making an elixir project for the first time. That is about the publish phase of a project...

This installation sections should really include solely.
Get started by running iex -S mix

your project name is the module put a capital letter of your project name and hit tab to autocomplete to the full module name.

put a . and hit tab a few more times to get autocomplete to expose the hello function.

type he and then tab to autocomplete.

and hit enter to see the function return :world.

^ or at least they should just put a link to if you are writing the library for the first time go here to this getting started link for mix.

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
<!--
Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at <https://hexdocs.pm/elixir_autocomplete_bug_on_mac_computer>.
-->
## Acknowledgement:
Shout out to [github.com/murjax](https://github.com/murjax) for finding the bug when I figured out how to get the autocomplete to sort by arity.

## Additional Reading
[the mac issue of folder names not sorting correctly](https://discussions.apple.com/thread/1317720)  
[regarding lexographic sort](https://softwareengineering.stackexchange.com/questions/127639/why-do-some-sorting-methods-sort-by-1-10-2-3)  
[preliminary research on changing LC_COLLATE, (very little time invested on this route so far.)](https://stackoverflow.com/questions/60296828/set-lc-collate-and-lc-ctype-on-macos)  
[looks like a promising LC_COLLATE example that I should try out.](https://apple.stackexchange.com/a/344960)  

## Possible solutions:
- change LC_COLLATE globally on the computer to sort differently by default.
- add some plugin addition to erlang that elixir can use to intercept the output of erlang shell and modify it at runtime to sort correctly.
- since I use bash, add a trap to key in on use of tab in the terminal and pipe the output to a sort.
- confirm erlang is doing the sort instead of the operating system and make the change to erlang itself.

## Get involved
Do you know a solution that I have not mentioned here or do you want to leave a comment about this project?  
Open a [github issue](https://github.com/MichaelDimmitt/ElixirAutocompleteBugOnMacComputer/issues) in the project to add to the discussion or make a pr proposing a change to the project. Thank you!
