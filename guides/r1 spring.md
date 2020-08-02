:beginner: **Recollect**

:point_right: Application Context
-  ClassPathXmlApplicationContext
-  AnnotationConfigApplicationContext
-  WebApplicationContext

:point_right: Bean Scopes

`for all spring applications`
- prototype
- singleton

`for web aware applications`
- request
- session
- global session

`CRUD TO HTTP VERBS MAPPING`  
CREATE (INSERT) = POST  
READ (SELECT) = GET  
UPDATE = PUT  
DELETE = DELETE  

:point_right: `architectures`

1. Layered architecture
2. MVC architecture
3. Service Oriented architecture (SOA)
4. Microservices Architecture

:point_right: Deep Dive into Reflection API and Custom Annotations with regards to Spring Framework

interface ProductService{
}

@Service
class ProductServiceImpl implements ProductService
{
}

class ProductController{
@Autowired
ProductService productService;
}

REFLECTION API + CUSTOM ANNOTATOINS:
ComponentScanning, BeanCreation, Wiring the Beans, Dependency Injection

1. scanning annotations
2. instantiating the beans
ProductService productService = new ProductServiceImpl();
3. putting it in the registry (ApplicationContext)
productService | new ProductServiceImpl()
4. provide the insance whereever required (getBean() method)
applicationContext.getBean("productService");
`


platform library framework

if(package.equals("com.live.controller"))
{
   throw new SecurityException("Reflection not working");
}