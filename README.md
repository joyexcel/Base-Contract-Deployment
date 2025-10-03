# Base-Contract-Deployment
Create a new code file with Remix https://remix.ethereum.org
Click on "New File" button, and name your file.
Paste code in Remix file editor
// SPDX-License-Identifier: MIT
/**
 * @custom:dev-run-script [VotingSample]
 */
pragma solidity ^0.8.0;

contract VotingSample {
    address public owner;
    string[] public candidates; 
    mapping(string => uint) public votes; 

    constructor(string[] memory _candidates) {
        owner = msg.sender;
        candidates = _candidates;
    }

    function voteForCandidate(string memory _candidate) public {
        require(isValidCandidate(_candidate), "Not a valid candidate");
        votes[_candidate] += 1;
    }

    function isValidCandidate(string memory _candidate) internal view returns (bool) {
        for(uint i = 0; i < candidates.length; i++) {
            if(keccak256(abi.encodePacked(candidates[i])) == keccak256(abi.encodePacked(_candidate))) {
                return true;
            }
        }
        return false;
    }
}
 Visit the "Solidity Compiler" and click on "Compile yourfilename.sol
        Paste the "custom dev-run-script..." string into the "string[] _Candidates" field.
        Click "Deploy" and wait for a successful deployment confirmation
