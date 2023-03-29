XR Scans NFT Contract
This Solidity contract defines a non-fungible token (NFT) setup for representing ownership of medical images, specifically for XR Scans by teleradiologyai. The contract is based on the ERC721 standard from OpenZeppelin, which is a widely used standard for NFTs on the Ethereum blockchain.

Contract Overview
The XRScansNFT contract defines a struct called Image that represents a medical image, with an ID, a URI that points to the location of the image file, a boolean flag indicating whether the image exists, and an address representing the current owner of the image. The contract uses two mappings to keep track of images: images, which maps image IDs to Image structs, and ownedImages, which maps owner addresses to arrays of image IDs that they own.

The contract has two main functions:

mint(string memory uri): Allows the contract owner to mint new images by passing in a URI that points to the location of the image file. The function creates a new Image struct with a unique ID and the provided URI, and adds it to the images mapping. It also mints a new NFT and assigns it to the contract owner, and adds the ID of the newly minted NFT to the ownedImages mapping for the contract owner. Finally, it emits an ImageCreated event with the image ID, URI, and owner address.
transferImage(uint256 id, address to): Allows the current owner of an image (which could be a patient or a healthcare provider) to transfer ownership of the image to another address. The function checks that the caller is either the owner or has been approved to transfer the NFT, and that the image actually exists. If these conditions are met, the function transfers ownership of the NFT and updates the owner field of the corresponding Image struct. It also emits an ImageTransferred event with the image ID, the previous owner address, and the new owner address.
The contract also inherits the Ownable contract from OpenZeppelin, which allows the contract owner to control certain functions.

Getting Started
To use this contract, you can deploy it to a local or public Ethereum network using a tool like Remix. Before deploying, you will need to import the ERC721 and Ownable contracts from OpenZeppelin by adding the following lines at the top of the Solidity file:

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

You can then compile and deploy the contract using Remix, specifying the contract name (XRScansNFT), the constructor arguments (a string for the contract name and a string for the contract symbol), and the desired network (e.g., the local development network, the Ropsten test network, or the Ethereum main network).

Once the contract is deployed, the contract owner can use the mint function to create new images, and any owner of an image can use the transferImage function to transfer ownership to another address. You can also use the getOwnedImages function to retrieve the image IDs owned by a particular address.

License
This contract is licensed under the MIT License.
