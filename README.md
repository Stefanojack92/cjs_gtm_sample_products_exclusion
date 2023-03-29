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

window.dataLayer.push({
  event: 'purchase',
  ecommerce: {
	
    currency: 'EUR',
    value: 212.00,
    tax: 3.00,
    shipping: 5.00,
    affiliation: 'My online shop',
    transaction_id: 'abc025',
    items: [{
      item_name: 'Product 1',
      item_id: 'product1',
      price: 12,
      item_brand: 'brand A',
      item_category: 'Apparel',
      item_category2: 'T-shirt',
      item_variant: 'Blue',
      quantity: '3',
    },{
      item_name: 'Product 2',
      item_id: 'product2',
      price: 0,
      item_brand: 'Brand B',
      item_category: 'Category B',
      item_variant: 'Yellow',
      quantity: '1'
    },{
      item_name: 'Product 3',
      item_id: 'product3',
      price: 24,
      item_brand: 'Brand B',
      item_category: 'Category B',
      item_variant: 'Yellow',
      quantity: '7'
    },{
      item_name: 'Product 4',
      item_id: 'product4',
      price: 0,
      item_brand: 'Brand B',
      item_category: 'Category B',
      item_variant: 'Yellow',
      quantity: '4'
    }]
  }
});


# Task

To solve this problem we have to iterate trough the whole array and check in every object for the price. If the value of price is equal to 0, it means we are facing a sample object. We have to sum the quantity of all objects that have a value > 0. I order to do that we create a custom javascript function in Google Tag Manager, in which following Function is running:

