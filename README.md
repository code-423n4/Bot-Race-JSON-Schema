# Bot-Race-JSON-Schema

## JSON Schema

------
example:
```
{
    "comment": "Hello all this is my sample bot ",
    "footnote": "Thanks for reading!",
    "findings": [
        {
            "severity": "Low",
            "title": "some other title",
            "description": "Example markdown description",
            "gasSavings": null,
            "category": null,
            "instances": [
                {
                    "content": "Example markdown content",
                    "loc": [
                        "[207](https://somepretentlinesofcode207.com)",
                        "[102](https://somepretentlinesofcode102.com)"
                    ]
                },
                {
                    "content": "Example markdown content",
                    "loc": [
                        "[202](https://somepretentlinesofcode202.com)"
                    ]
                }
            ]
        },
        {
            "severity": "Medium",
            "title": "Unchecked return value of low-level",
            "description": "Example markdown description",
            "gasSavings": null,
            "category": "some category",
            "instances": [
                {
                    "content": "Example markdown content",
                    "loc": [
                        "[108](https://somepretentlinesofcode108.com)"
                    ]
                }
            ]
        }
    ]
}
```

## Details

-------

comment : **Optional** - string/null

footnote: **Optional** - string/null

findings: **Mandatory** - array of issues found

severity   : **Mandatory** - string 
   
title      : **Mandatory** - string
   
description: **Mandatory** - string
   
gasSavings : **Optional** - number/null. Total gas savings for the individual issue. If you wish to include the individual gas saving for each instance, please add that into the `content` section of the instances.
  
category   : **Optional** - string/null. Not currently in use, but may become required in future.
  
instances  : **Mandatory** - an array of instances. Supports either blocks of instances, or each instance in the array as its own instance.

content : **Mandatory** - string; this is where the content, code snippets, @audit tags, and the file would need to be. You may choose to stack all content for an individual file here as a block, or treat it as an individual instance. If you wish to treat these as seperate instances instead of a block of instances, and you want the file to be present for each instance, please ensure that you include this in the content of each issue.

### examples:

&nbsp;&nbsp;&nbsp;&nbsp;"content" : "\```solidity<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// @notice Transfer ownership of an NFT -- THE CALLER IS RESPONSIBLE<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;///  TO CONFIRM THAT `_to` IS CAPABLE OF RECEIVING NFTS OR ELSE<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;///  THEY MAY BE PERMANENTLY LOST<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// @dev Throws unless `msg.sender` is the current owner, an authorized<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;///  operator, or the approved address for this NFT. Throws if `_from` is<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;///  not the current owner. Throws if `_to` is the zero address. Throws if<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;///  `_tokenId` is not a valid NFT.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// @param _from The current owner of the NFT<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// @param _to The new owner<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// @param _tokenId The NFT to transfer<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;function transferFrom(address _from, address _to, uint256 _tokenId) external payable;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\```"
               
&nbsp;&nbsp;&nbsp;&nbsp;"content" : "\```solidity<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;File: src/BranchBridgeAgentExecutor.sol
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;53:      function executeNoSettlement(address _router, bytes calldata _payload) external payable onlyOwner {
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;66       function executeWithSettlement(address _recipient, address _router, bytes calldata _payload)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;67           external<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;68           payable<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;69           onlyOwner<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;70:      {
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;104      function executeWithSettlementMultiple(address _recipient, address _router, bytes calldata _payload)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;105          external<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;106          payable<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;107          onlyOwner<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;108:     {
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\```"
  
loc     : **Mandatory** - an array of lines of code for this instance. This value will be used to calculate the total instances, when generating the report.

### examples:

&nbsp;&nbsp;&nbsp;&nbsp;"loc" : ["\[53\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c8/src/BranchBridgeAgentExecutor.sol#L53-L53)", "\[66\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c86/src/BranchBridgeAgentExecutor.sol#L66-L70)", "\[104\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c86/src/BranchBridgeAgentExecutor.sol#L104-L108)"]
				
