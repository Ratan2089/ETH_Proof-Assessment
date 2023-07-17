pragma solidity 0.8.18;
//This line specifies the version of Solidity that the contract is written in. In this case, it's version 0.8.18. 
The pragma statement ensures that the contract is compiled using a specific version or a compatible version of the Solidity compiler.

contract MyToken {
//This line declares the start of the contract named MyToken.

    // public variables here
    string public tokenName = "myToken";
    string public tokenAbbvr = "TOKEN";
    uint public totalSupply = 0;

//These lines declare public variables that can be accessed by anyone interacting with the contract. The tokenName variable 
represents the name of the token (set to "myToken" in this case), tokenAbbvr represents the abbreviation of the token
(set to "TOKEN"), and totalSupply represents the total supply of tokens (initialized to 0).


    // mapping variable here
    mapping(address=>uint) public balances;

//This line declares a mapping variable named balances. It maps addresses to unsigned integers (uint) and is used to
keep track of the token balances of different addresses. By declaring it as public, Solidity automatically generates
a getter function balances() that allows external access to retrieve the balance of a specific address.


    // mint function
    function mint(address _address, uint _value) public{
        totalSupply+=_value;
        balances[_address] += _value;
    }

//This function allows the contract owner to mint (create) new tokens and assign them to a specific address. 
The function takes two parameters: _address represents the address to which the tokens will be assigned, 
and _value represents the amount of tokens to be minted. The function increases the totalSupply by the minted
amount and adds the minted tokens to the balance of the specified address.



    // burn function
    function burn(address _address, uint _value) public{
        if (balances[_address] >= _value)
        {
        totalSupply-=_value;
        balances[_address] -= _value;
        }

//This function allows the contract owner to burn (destroy) existing tokens from a specific address. 
The function takes two parameters: _address represents the address from which the tokens will be burned, 
and _value represents the amount of tokens to be burned. Before burning the tokens, the function checks if
the specified address has a sufficient balance. If the condition is met, the function subtracts the burned
tokens from the totalSupply and updates the balance of the specified address.
    }
}
