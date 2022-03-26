# Artist information

## Code archival

The official on-chain code repository for the gm.studio was deployed to [0x8229e9bc30cb02c2d9af25022bc146a302c48c47](https://etherscan.io/address/0x8229e9bc30cb02c2d9af25022bc146a302c48c47#readContract).
This repository is used to store the code for all on-chain collections and acts as a central database thereof.

### Storing in contract bytecode

_This step is usually done by the studio team_

- generate a gzipped tarball of all files
  - `tar -czf archive.tar.gz sketch.min.js desc.json`
- get the blob's hex string e.g. by `echo "0x"$(hexdump archive.tar.gz -v -e '/1 "%02X"')`
- store blob using `repo.store(blob)`
  - an event containing the storage address will be emitted during the transaction

### Code verification

Please double-check and make sure that the stored code matches the one used for rendering the tokens.

The code can be either fetched directly from the contract using the `repo.getBlob(collectionAddress)` or more conveniently using the tool under [gmstudio.art/repo](https://www.gmstudio.art/repo).

- Connect a wallet (needed to get a connection to the blockchain)
- Make sure to select the correct collection address
- Click `Download Blob` to download the code archive
- Unpack the archive

Please verify that the stored script is correct e.g. by rerendering the genesis token using the downloaded code. 

### Code signature

If the stored code is correct, you can proceed to sign the repository entry (this step is optional but we highly encourage to do so).

- Connect the wallet that you want to use to sign the code entry.
- Make sure to select the correct collection address
- Click `Sign`
- Metamask will pop up and prompt you to sign something - please do so.
  - Even though some of the characters might seem weird, this is totally fine because we are signing the raw binary hash of the repository entry while Metamask tries to interpret it as a string.
- Please communicate the output appearing below the buttons to the studio team.
