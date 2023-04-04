+++
title = "MetaLadsAI NFT developer"
date = "2022-11-18"
author = "Bogdan Munteanu"
description = "Main developer for an NFT collection"
+++

As the main developer of an NFT collection, I have created a platform that could automatically buy NFTs from a variety of marketplaces from the Solana blockchain for users, only if they were in concordance with a set of filters that they selected (rarity, price, collection name). I have done this using JavaScript in the form of jQuery, HTML and CSS.

The new listings were fetched by the CoralCube API, the serialisation of the transaction was done using the Solana Web3js NPM library, and in the end it was 'sent' to the blockchain using the MagicEden API.

There were also various steps in between the aforementioned ones, such as filtering the Rarities, Prices, etc., providing autocomplete for the collection name, and perhaps most important of all, the authentication.

The authentication was done with the help of Solana Wallet, and access was restricted for those who did not own an NFT made by MetaLadsAI.

I have also worked on implementing an NFT staking solution for Solana (Cardinal Staking), and also generating a reward token using the Solana CLI.

