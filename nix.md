to enter or leave a nix env

#nix dev env
nix develop - activates a nix environment defined in a local flake
nix run - run software with no installation

when multiuser login everytime run something for nix do:
sudo -i <home-manager> <packages>

https://www.youtube.com/watch?v=utoj6annRK0
i followed the vid above

# Wrangling Flake Inputs

The flake input schema allows for:

1.  Having your flake pull in _another flake_ as an input
2.  Having your flake pull in an input that is specified by _another flake_
3.  Forcing _another flake_ to use an input specified in your flake
4.  Forcing _another flake_ to use an input specified by **yet a different flake**

being aware can be useful to ensure all inputs agree on the same dep
