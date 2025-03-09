Self questions:


- How to keep yourself updated with latest technologies? - 

- In kafka, if message is not delivered then how you can debug it or clearing the queue
- Multithreading use case
- CircuitBreaker configuration like timing and retry time
- Where do you used list, map, set
- What you check when you are reviewing the code?
- Ever used @scope annotation?
- Used @qualifier annotation?
- 2 db
- FlatMap

Realtime example:

### Functional interface:
Custom Transformation Logic using Transformer with transform method (convertToDTO)
  
        @FunctionalInterface
        public interface Transformer<T, R> {
            R transform(T t);
        }

        // Usage in a service class
        @Service
        public class MyService {

            private final Transformer<User, UserDTO> userTransformer;

            public MyService(Transformer<User, UserDTO> userTransformer) {
                this.userTransformer = userTransformer;
            }

            public UserDTO convertToDTO(User user) {
                return userTransformer.transform(user);
            }
        }

        @Component 
        public class UserTransformer implements Transformer<User, UserDTO> { 
            @Override 
            public UserDTO transform(User user) { 
                return new UserDTO(user.getId(), user.getName(), user.getEmail()); 
            } 
        }


### Stream
RestControllerAdvice - MethodArugmentNotFoundExceptions(Stream)

        Optional<List<Account>> accounts = accountRepo.findByCustId(customerId);
		List<Long> accountNumbers = accounts
		        .map(list -> list.stream()
		                .map(Account::getAccountNumber)
		                .collect(Collectors.toList()))
		        .orElseGet(ArrayList::new);

Merge two list -

        // Initialize productList and discountList with some example data
        List<Product> productList = new ArrayList<>();
        productList.add(new Product(1, "Laptop", 1500.00));
        productList.add(new Product(2, "Smartphone", 800.00));

        List<Discount> discountList = new ArrayList<>();
        discountList.add(new Discount(1, "Black Friday", 20.0));
        discountList.add(new Discount(3, "Cyber Monday", 15.0));  // No matching product

        // Merge lists using streams
        List<ProductDetail> productDetails = productList.stream()
            .flatMap(product -> discountList.stream()
                .filter(discount -> discount.getProductId() == product.getProductId())
                .map(discount -> new ProductDetail(product, discount)))
            .collect(Collectors.toList());

        // Print the merged list
        productDetails.forEach(System.out::println);
        

### Lambda
RestControllerAdvice - MethodArugmentNotFoundExceptions(Stream)

### Interface default method
### Interface static method
### Optional
### Date and Time: 
- java.util.Date represents both date and time in a single object, which can be confusing and
 lead to errors.
- java.util.Date does not handle time zones properly. It always represents time in UTC, and
 converting it to local time zones requires additional calculations.


Old -> 

        import java.text.SimpleDateFormat;
        import java.util.Calendar;
        import java.util.TimeZone;

        public class OldApiExample {
            public static void main(String[] args) {
                TimeZone timeZone = TimeZone.getTimeZone("Europe/Paris");
                Calendar calendar = Calendar.getInstance(timeZone);
                SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss z");
                dateFormat.setTimeZone(timeZone);
                String formattedDate = dateFormat.format(calendar.getTime());
                System.out.println("Current date and time in Paris: " + formattedDate);
            }
        }

New ->

        import java.time.ZonedDateTime;
        import java.time.format.DateTimeFormatter;
        import java.time.ZoneId;

        public class NewApiExample {
            public static void main(String[] args) {
                ZonedDateTime parisDateTime = ZonedDateTime.now(ZoneId.of("Europe/Paris"));
                DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss z");
                String formattedDate = parisDateTime.format(formatter);
                System.out.println("Current date and time in Paris: " + formattedDate);
            }
        }


ConcurrentHashMap
CompleteableFuture
ThreadPoolExecutorService
Batch jobs


### ThreadPoolTaskExecutor:
- setCorePoolSize() = Number of CPU cores(Windows - Task manager, Linux - lscpu, nproc, AWS - EC2 )
- setMaxPoolSize() = 2 * setCorePoolSize() (for IO-heavy tasks)
- setQueueCapacity() = Small value (e.g., 50 tasks) initially.
- Understanding the Parameters:
    - TaskType 
        - CPU intensive(Require more processing power and fewer threads to avoid excessive context switching)
        - IO-bound tasks(Can support more threads since these tasks spend significant time waiting (e.g., for network or disk operations).
    - TaskDuration 
        - If tasks are short-lived, the thread pool can process more tasks with fewer threads.
        - For long-running tasks, increase the thread pool size or queue capacity to handle higher task volume.


### Questions:
- instance variables, constructor, static block
- We are doing batch jobs and sending bunch of records using resttemplate/feign/webclient, if there are any failure for some of the records then how will you retrigger it, what is retry mechanism or handling failure cases - use batch to decrase db throughput and to reduce db calls
- How to handle versioning? best option? URL versioning vs Header versioning vs Parameter versioning 


### Strategy design pattern:
- Having same code in derived classes but not available in base class, which can result into duplicate code. We can create dynamic object and use them into derived classes
