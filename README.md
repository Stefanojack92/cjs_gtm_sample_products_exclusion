# cjs_gtm_sample_products_exclusion

Custom Javascript variable for sample product exclusion of an E-Commerce Datalayer

# Scenario

An E-Commerce website owner, selling parquet flooring has 2 types of products on stock:

1- Regular parquet pieces

2- Free wooden samples

The selling of regular parquet pieces generates the revenue of the E-Commerce. Customers can also order free wooden samples, to choose among a large collections of colours and materials.

The customer has implemented Google Tag Manager and Google Analytics 4 on his website to track E-Commerce Data.

As the free wooden samples are not relevant for generating revenue, the customer wants to make a personalisation to his tracking code on the website. The idea is to send to Google Analytics the sum of all the products, that are generating value for the online shop.

The quantity of all sample products that are added to the purchase should not be sent to GA4.

After the purchase event is fired a datalayer like this one is pushed to Google Tag Manager:

