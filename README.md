# MongoDB Query Guide
This document outlines the MongoDB queries for common product-related operations, including retrieving, filtering, and deleting data from the products collection. Each query is explained in detail along with the corresponding MongoDB syntax.

## 1. Find All Information About Each Product
Retrieve all the documents from the products collection.
db.products.find();

## 2. Find Products with Price Between 400 to 800
Retrieve all products where the product_price is greater than 400 and less than 800.
db.products.find({ $and: [ { 'product_price': { $gt: 400 } }, { 'product_price': { $lt: 800 } } ] });

## 3. Find Products with Price Not Between 400 to 600
Retrieve all products where the product_price is less than 400 or greater than 600.
db.products.find({ $or: [ { 'product_price': { $lt: 400 } }, { 'product_price': { $gt: 600 } } ] });

## 4. List Four Products with Price Greater Than 500
Retrieve the first four products where the product_price is greater than or equal to 500.
db.products.find({ 'product_price': { $gte: 500 } }).limit(4);

## 5. Find the Product Name and Material of Each Product
Retrieve only the product_name and product_material fields for all products.
db.products.find({}, { 'product_name': 1, 'product_material': 1 });

## 6. Find the Product with an ID of 10
Retrieve the product document where the id is equal to "10".
db.products.findOne({ 'id': { $eq: "10" } });

## 7. Find Only the Product Name and Material
Retrieve only the product_name and product_material fields, excluding the _id field, for all products.
db.products.find({}, { 'product_name': 1, 'product_material': 1, '_id': 0 });

## 8. Find All Products with Material Containing "Soft"
Retrieve all products where the product_material is equal to "Soft".
db.products.find({ 'product_material': { $eq: 'Soft' } });

## 9. Find Products with Color "Indigo" or Price 492.00
Retrieve all products where the product_color is "indigo" or the product_price is 492.00.
db.products.find({ $or: [ { "product_color": { $eq: 'indigo' } }, { "product_price": { $eq: 492.00 } } ] });

## 10. Delete Products with Price Value of 28
Delete a single product where the product_price is equal to 28.00.
db.products.deleteOne({ "product_price": { $eq: 28.00 } });

# Summary:
This guide provides queries for various use cases including finding, filtering, and deleting documents from a MongoDB products collection. Each query is structured using proper field names and MongoDB operators to perform the desired actions efficiently.
