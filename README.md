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
            "description": "Example markdown decsription",
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
            "description": "Example markdown decsription",
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

findings: **Mandatory** - is an array of issues found.

severity   : **Manditory** - string 
   
title      : **Manditory** - string
   
description: **Manditory** - string
   
gasSavings : **Optional** - number/null - This is for the total gas saving for the individual issue. If you wish to have the individual gas saving for each instance pleas add that into the content section of the instances.
  
category   : **Optional** - string/null this is not currently used but as there is discussion on the use of issue categories there is potential for this field to become required.
  
instances  : **Manditory** - an array is instances, this can be thought of in two ways. One as blocks of instances or each instance in the array as it's own instance.

content : **Manditory** - string, this is where the content, code snippets, @augit tags, and the file would need be. Depending on if you wish to stack all content for an individual file here as a block or treat it as an individual instance. If you are wishing to treat these as seperate instances instead of a block of instances and you wish to the file to be present for each instance please make sure that you had this in the content of each issue.

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
  
loc     : **Manditory** - an array of lines of code for this instance. This is is where the total instances will be calculated from when the report is generated.

### examples:

&nbsp;&nbsp;&nbsp;&nbsp;"loc" : ["\[53\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c8/src/BranchBridgeAgentExecutor.sol#L53-L53)", "\[66\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c86/src/BranchBridgeAgentExecutor.sol#L66-L70)", "\[104\](https://github.com/code-423n4/2023-09-dev-test/blob/6c21f6b739252367c5fe770fed3ff76eb3ca2c86/src/BranchBridgeAgentExecutor.sol#L104-L108)"]
				
