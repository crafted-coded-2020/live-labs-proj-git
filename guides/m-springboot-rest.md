:beginner: **CRUD with RESTful Application**  

:point_right: GET operation  

:one: create spring boot starter project  
:two: configure web dependency
```xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
```
:three: create model  
```java
package com.live.model;

public class Product {
	private Long productId;
	private String productName;
	private String productDescription;
	private String price;
	public Product(Long productId, String productName, String productDescription, String price) {
		super();
		this.productId = productId;
		this.productName = productName;
		this.productDescription = productDescription;
		this.price = price;
	}
	public Product() {
		super();
	}
	public Long getProductId() {
		return productId;
	}
	public void setProductId(Long productId) {
		this.productId = productId;
	}
	public String getProductName() {
		return productName;
	}
	public void setProductName(String productName) {
		this.productName = productName;
	}
	public String getProductDescription() {
		return productDescription;
	}
	public void setProductDescription(String productDescription) {
		this.productDescription = productDescription;
	}
	public String getPrice() {
		return price;
	}
	public void setPrice(String price) {
		this.price = price;
	}
}

```
:four: create the controller
```java
package com.live.controller;

import java.util.ArrayList;
import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import com.live.model.Product;

@RestController
public class ProductController {
	@GetMapping("/products")
	public List<Product> getProducts() {
		List<Product> products = new ArrayList<Product>();
		products.add(new Product(100l,"SpringBoot","Book",500.50f));
		products.add(new Product(101l,"Angular","Book",555.50f));
		return products;
	}
}
```
:five: access the page
```html
http://localhost:8081/products
```
:six: verify results  
 
```json
[{"productId":100,"productName":"SpringBoot","productDescription":"Book","price":500.5},{"productId":101,"productName":"Angular","productDescription":"Book","price":555.5}]
```
