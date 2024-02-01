pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract MyNFT is ERC721 {
    constructor()
        ERC721("MyNFT", "MNFT")
    {}
    
    struct File {
        string fileType;      
        string fileName; 
    }
    
    mapping(uint256 => File) public files;
    
    function mint(address owner, string memory fileType, string memory fileName) public returns (uint256 tokenId) {
        _tokenIds.increment();
        
        tokenId = _tokenIds.current();
        _mint(owner, tokenId);
        
        files[tokenId] = File(fileType, fileName);
        
        return tokenId;
    }
}
