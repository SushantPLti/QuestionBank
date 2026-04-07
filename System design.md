## Low Level Design(LLD)

- It majorly focuses on classes and objects within a system
- HLD -> LLD -> Actual code

### Goals
- To write the clean code
- Code should be flexible and maintanable
- Code should be easy to test

### Categories
- Creational: Controls the object creation
    - Singleton
    - Builder
    - Factory
    - Abstract Factory
    - Object Pool
    - Prototype
- Structural: It focuses on, how different classes/objects are arranged together so that larger problem can be solved in most flexible way
    - Decorator
    - Proxy
    - Composite
    - Adapter
    - Bridge
    - Facade
    - Flyweight
- Behavioral: it focuses on, how different objects communicate or interact with each other.(In other words, with above structural pattern we created the skeleton of the system but how the skeleton behaves like coordination, responsibility, interaction is all guided by behavioral pattern)
    - State
    - Strategy
    - Observer
    - Chain of responsibility
    - Template
    - Iterator
    - Interpreter
    - Command
    - Visitor
    - Mediator
    - Memento
    - Null object




##Liskov substituion:

        class BankAccount {
            void withdraw(double amount) {
                System.out.println("Withdrawing money");
            }
        }
        class FixedDepositAccount extends BankAccount {
            @Override
            void withdraw(double amount) {
                throw new UnsupportedOperationException("Cannot withdraw before maturity");
            }
        }

        //Why this breaks LSP
        void processWithdrawal(BankAccount account) {
            account.withdraw(1000);  // 💥 fails for FixedDepositAccount
        }

Solution:
        interface Account {
            double getBalance();
        }

        interface Account {
            double getBalance();
        }

        class SavingsAccount implements Account, Withdrawable {
            @Override
            public void withdraw(double amount) {
                System.out.println("Withdrawn " + amount);
            }

            @Override
            public double getBalance() {
                return 50000;
            }
        }

        class FixedDepositAccount implements Account {
            @Override
            public double getBalance() {
                return 200000;
            }
        }

- Why this follows LSP
    - No false promises
    - No disabled functionality
    - Business rules are respected
        
        void withdrawMoney(Withdrawable account) {
            account.withdraw(1000);
        }

- Another Ecommerce ex

        class Payment {
            void payOnline() {
                System.out.println("Online payment");
            }
        }

        class CashOnDeliveryPayment extends Payment {
            @Override
            void payOnline() {
                throw new UnsupportedOperationException("COD does not support online payment");
            }
        }

Solution:

        interface Payment {
            void pay();
        }

        class OnlinePayment implements Payment {
            public void pay() {
                System.out.println("Paid online");
            }
        }

        class CashOnDeliveryPayment implements Payment {
            public void pay() {
                System.out.println("Pay on delivery");
            }
        }



2. SOLID Principles
https://drive.google.com/drive/folders/1h1FwjAp4b29TrPhyjaChEUgR7JZ0K6Fh?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/video1solid?ref_type=heads

3. Liskov Substitution Principle (LSP) Solution
https://drive.google.com/file/d/1KusquKOSzFIWFCZAdiXJCK-nrB-5yM-j/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/video1solid?ref_type=heads

4. Strategy Design Pattern (Behavioral Pattern)
https://drive.google.com/file/d/1OEHj80lVMzN2r4zk_oamiaQ0H1Vdqr0A/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/strategy?ref_type=heads

5. Observer Pattern (Behavioral Pattern)
https://drive.google.com/file/d/1OnmM2se29pTWgpdqEebCW87RN2a4zr9o/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/observer?ref_type=heads

6. Decorator Design Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1F2E2_zMvUQHISJbQhVrfuhTLY_yovDBX/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/decorator?ref_type=heads

7. Factory & Abstract Factory pattern (Creational Design Pattern)
https://drive.google.com/file/d/1CcX055go211A_63ZLT0ug15CgyqkkpTj/view?usp=drive_link
https://drive.google.com/file/d/1eHkU_2MrD9P3j67xfHO2BtJ4bVzosvdl/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/creationalpatterns/factory?ref_type=heads
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/creationalpatterns/abstractfactory?ref_type=heads

8. Design Parking Lot (English Dubbed)
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/interviewquestions/parking_lot?ref_type=heads

9. Design Tic-Tac-Toe Game
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/interviewquestions/tictactoe?ref_type=heads

10. LLD of Elevator System
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/interviewquestions/elevator?ref_type=heads

11. LLD of Car Rental System
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/interviewquestions/carrental?ref_type=heads

12. Chain Of Responsibility Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1s18DKvYNZCL_wam2z3nxHK9UDZ9mQmG6/view?usp=sharing
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/chainofresponsibility?ref_type=heads

13. LLD of Snake n Ladder Game
https://gitlab.com/shrayansh8/interviewcodingpractise/-/tree/main/src/main/java/com/conceptandcoding/LowLevelDesign/LLDSnakeLadder?ref_type=heads

14. Proxy Design Pattern (Structural Pattern)
https://drive.google.com/file/d/1mq3yqb_QKf7Q156rrfQ-yWhD9-YQU__H/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/proxy

15. LLD of BookMyShow | Design Movie Ticket Booking App
https://drive.google.com/file/d/1XbWo8m1hOOdKGww0UO1x3zIskdQjqf2i/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/interviewquestions/book_my_show?ref_type=heads

16. Null Object Design Pattern (Behavioral Pattern)
https://drive.google.com/file/d/1NWepC7duIoqI6FrnggcGG5fPaYtKS_hm/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main

17. State Design Pattern (Behavioral) | Design Vending Machine
https://drive.google.com/file/d/1DCHCr3TxXm_XxNA5zd38UeKYj1bu8GMZ/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/state?ref_type=heads

18. LLD of ATM
https://gitlab.com/shrayansh8/interviewcodingpractise/-/tree/main/src/main/java/com/conceptandcoding/LowLevelDesign/DesignATM?ref_type=heads

19. Composite Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1niida4cw_OnLf0-VQgouGvIfAGcoZBVs/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/composite?ref_type=heads

20. Adapter Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1F50CpCcVq0AqxAbnMZdwLrJpQY2A7BLZ/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/adapter?ref_type=heads

21. LLD of Splitwise
https://gitlab.com/shrayansh8/interviewcodingpractise/-/tree/main/src/main/java/com/conceptandcoding/LowLevelDesign/DesignSplitwise?ref_type=heads

22. Builder Design Pattern (Creational Design Pattern)
https://drive.google.com/file/d/16xhiKSGlEbrQMIQNe6fzOnCKyWbmG5tS/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/creationalpatterns/builder?ref_type=heads

23. LLD of Cricbuzz
https://gitlab.com/shrayansh8/interviewcodingpractise/-/tree/main/src/main/java/com/conceptandcoding/LowLevelDesign/LLDCricbuzz?ref_type=heads

24. Facade Design Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1FyX9SqEj_w6GnfBEzadDIP8hFAyUrdta/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/facade?ref_type=heads

25. Bridge Design Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1NVlJDE3PTYG0-9ePA0zI_wDGamJp7EFR/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/bridge?ref_type=heads

26. LLD of Inventory Management System
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/bridge?ref_type=heads

27. Flyweight Design Pattern (Structural Design Pattern)
https://drive.google.com/file/d/1SRbXKrENtQHGiuU_dyWsbvF_NOR1aMpr/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/structuralpatterns/bridge?ref_type=heads

28. Command Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1A71zSq-HMYu-iDWNBLBUqmnJxwlRe2ov/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/command?ref_type=heads

29. Iterator Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1iWSDKXJWgwAJtYxv8UKEOWxR4ibDMEQ8/view?usp=drive_link

30. Mediator Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1HVWmLHzSwcGlEUUR_nxdilDnDo7rK2Eo/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/mediator?ref_type=heads

31. LLD of Apply Coupons on Shopping Cart Products

32. Visitor Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1iWSDKXJWgwAJtYxv8UKEOWxR4ibDMEQ8/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/visitor?ref_type=heads

33. MVC Design Pattern
https://drive.google.com/file/d/1oKEaL_-2SnfeRIJUDzX7WNEOtqqcMTJ0/view?usp=drive_link

34. Memento Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1tHHVaWBVwS2-41vDhKhM_BPCgA7ZXjEN/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/memento?ref_type=heads

35. Template Method Design Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1f1T9zvHw0fEX601O0L64rH8ZZ5qr-srk/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/templatemethod?ref_type=heads

36. Interpreter Pattern (Behavioral Design Pattern)
https://drive.google.com/file/d/1vS8C1d1FXX35aCjYpr2AXIeLk5cS7gdk/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/behavioralpatterns/interpreter?ref_type=heads

37. LLD of Payment Gateway
https://notebook.zohopublic.in/public/notes/bietv6993f5a023ec4e9f89436149ac3ed2f7


38. Object Pool Design Pattern (Creational Design Pattern)
https://notebook.zohopublic.in/public/notes/dcr5za494c035adb441818e2bc20485b4de58
https://drive.google.com/file/d/1cqM72J44q1iwtsLWj99UGFAjDQe-m1mO/view?usp=drive_link
https://gitlab.com/shrayansh8/lld-lowleveldesign/-/tree/main/src/main/java/com/conceptcoding/creationalpatterns/objectpool?ref_type=heads

HLD
39. Network Protocols (English Dubbed) | Better with 1.25x playback speed
https://drive.google.com/file/d/1iegvlzgcLJtcGvbjJbPqF4hZaB5u_nrh/view?usp=drive_link

40. CAP Theorem (English Dubbed) | Better with 1.25x playback speed
https://drive.google.com/file/d/1rEs7p_Hrgdu57xakTyxgO1k3Zyp3zu-C/view?usp=drive_link

41. Introduction: Microservices (English Dubbed) | Better with 1.25x playback speed
https://drive.google.com/file/d/1d8R5wkQo9gnCcB_e2DFKCn-TgxWoJMsd/view?usp=drive_link

42. Microservices Patterns: SAGA Pattern, Strangler Pattern (English Dubbed)
https://drive.google.com/file/d/1d8R5wkQo9gnCcB_e2DFKCn-TgxWoJMsd/view?usp=drive_link

43. Scale from ZERO to MILLION User (English Dub) | Better with 1.25x playback speed
https://drive.google.com/file/d/16FIwh_zZ2nowjFh_vzeUq7nAwoaQct6f/view?usp=drive_link

44. Consistent Hashing (English Dubbed) | Better with 1.25x playback speed
https://drive.google.com/file/d/1dMSY_fHaKwADw_zeQJfoWQUiHwgwDL6H/view?usp=drive_link

45. Design URL Shortening Service like TinyURL
https://drive.google.com/file/d/1iegvlzgcLJtcGvbjJbPqF4hZaB5u_nrh/view?usp=drive_link

46. Back-Of-The-Envelope Estimation for System Design Interview
https://drive.google.com/file/d/1AH37a-iSXNquC01PUIi14yDO8jscnaA6/view?usp=drive_link

47. Design a Key-Value Store || Dynamo DB
https://drive.google.com/file/d/1iegvlzgcLJtcGvbjJbPqF4hZaB5u_nrh/view?usp=drive_link

48. SQL vs NoSQL
https://drive.google.com/file/d/1CuxKzs00W6meH_6PdF2la8xBkXnyvhcO/view?usp=drive_link

49. Whatsapp System Design
https://drive.google.com/file/d/1iegvlzgcLJtcGvbjJbPqF4hZaB5u_nrh/view?usp=drive_link

50. Design Rate Limiter
https://drive.google.com/file/d/1EwfhhSiBNJw87tqvoaseW5ZKUKB-YJDx/view?usp=drive_link

51. Design Idempotent POST API || Handle Duplicate Request by Idempotency Handler
https://drive.google.com/file/d/1pzl_Pr0iUD3jyRUtS58Sq9DyCsrr2dmE/view?usp=drive_link

52. Design High Availability System || Active Passive & Active Active Architecture
https://drive.google.com/file/d/1k7OUopYnC2fpEHDLw-zbFDdyNvoba4mo/view?usp=drive_link

53. Distributed Messaging Queue | Design Messaging Queue like Kafka, RabbitMQ
https://drive.google.com/file/d/1k7OUopYnC2fpEHDLw-zbFDdyNvoba4mo/view?usp=drive_link

54. Proxy vs Reverse Proxy

55. Load Balancer and Different Algorithms
https://notebook.zohopublic.in/public/notes/u3i1s15cb99da63b248e6a87bbbaaaef17751

56. Distributed Cache & Caching Strategies | Cache-Aside, Write-Through, Write-Back
https://notebook.zohopublic.in/public/notes/u3i1s15cb99da63b248e6a87bbbaaaef17751

57. Handle Distributed Transactions | Two-Phase Commit (2PC), 3PC and SAGA Pattern
https://notebook.zohopublic.in/public/notes/u3i1sc0949c83b482441887cc4eba8031560e

58. Database Indexing: B+ Tree, Data Page, Clustered and Non-Clustered Indexing
https://notebook.zohopublic.in/public/notes/74tdo7871dd86eb99414bb94d8737a8b73b84

59. Concurrency Control in Distributed System | Optimistic & Pessimistic Concurrency
https://notebook.zohopublic.in/public/notes/u3i1s8441ef17edee467bb020cc6974b3d7f9

60. Two Phase Locking (2PL)
https://notebook.zohopublic.in/public/notes/74tdoc7e4be4e091e4005916a9721b69ee7b3

61. OAuth 2.0 expalined
https://notebook.zohopublic.in/public/notes/bietv949cfd82a5804e0ea1d18400d3ff6fa3
https://youtu.be/3Gx3e3eLKrg?si=DdiZisU2_Xj6jbrd

62. Symmetric & Asymmetric Encryption with Explanation of AES, Diffie-Hellman
https://notebook.zohopublic.in/public/notes/bietvf603d76e50a04c989bb3522c763be0ee

63. JWT: JSON Web Token
https://notebook.zohopublic.in/public/notes/bietvcd2cffdd8c7d449c839c007fecf8d562

64. Thundering Herd Problem | Why Ticket Booking App goes down during peak traffic?
https://drive.google.com/file/d/1s_rhkuSserKURoOTwolrnMGifGHd9oKI/view?usp=drive_link

65. API GATEWAY and Microservices Architecture
https://notebook.zohopublic.in/public/notes/9wn9of886c95da92e4778b0d3bc23cb0b8106

66. Service Mesh and its Architecture in Microservices
https://notebook.zohopublic.in/public/notes/9wn9od9ab6075a35b4258aadedbf53aca805e

67. How DNS works? | System Design of Domain Name System
https://notebook.zohopublic.in/public/notes/9wn9oa7b313dd344b426288e0efca9f0eeaa6

68. In How many Microservices we should divide Monolithic System


69. Attacks with Demo | CSRF, XSS, CORS and SQL Injection
https://notebook.zohopublic.in/public/notes/9wn9oa7b313dd344b426288e0efca9f0eeaa6

70. Dual Write Problem | Event Driven Microservices Patterns
https://1drv.ms/o/c/6b364628c29feb52/EksLbbBuPIhDjFYNjtEw6kEB7wRxe5wd2oWXREL9gKphEg

71. Service Discovery Introduction
https://onedrive.live.com/view.aspx?resid=6B364628C29FEB52%21s9263727369a94fcd83cbce0c0db8053c&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New+Section+1.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FService+Discovery%7Cbe9efdfc-f515-344f-b765-9b58c71e6cdb%2F%29&wdorigin=703&wdpartid=%7B1d6ee994-9a33-9e49-9efe-8d00ba724950%7D%7B1%7D&wdsectionfileid=6b364628c29feb52%21s1965afa38c4142d88d16f8c0aad11692

72. Rate Limiter Algorithms
https://onedrive.live.com/view.aspx?resid=6B364628C29FEB52%21s9263727369a94fcd83cbce0c0db8053c&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New+Section+1.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FResilience4j+Building+Fault-Tolerant+Microservice%7Ca0095666-1317-4f4c-b672-a8915839634d%2F%29&wdorigin=703&wdpartid=%7B33040e75-114a-e603-3e60-15ff88227e15%7D%7B1%7D&wdsectionfileid=6b364628c29feb52%21s1965afa38c4142d88d16f8c0aad11692

73. Bulkhead Pattern Introduction
https://onedrive.live.com/view.aspx?resid=6B364628C29FEB52%21s9263727369a94fcd83cbce0c0db8053c&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New+Section+1.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FBulkhead+Fault-Tolerant+Microservice+%28Part-2%5C%29%7Cc82898a8-8c19-df43-a956-00d6d5ce44fc%2F%29&wdorigin=703&wdpartid=%7B275c27b2-26cb-c609-3c5c-06e012553b64%7D%7B1%7D&wdsectionfileid=6b364628c29feb52%21s1965afa38c4142d88d16f8c0aad11692

74. Retry Pattern : Fault Tolerance in Distributed Microservices
https://onedrive.live.com/view.aspx?resid=6B364628C29FEB52%21s9263727369a94fcd83cbce0c0db8053c&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New+Section+1.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FBulkhead+Fault-Tolerant+Microservice+%28Part-2%5C%29%7Cc82898a8-8c19-df43-a956-00d6d5ce44fc%2F%29&wdorigin=703&wdpartid=%7B275c27b2-26cb-c609-3c5c-06e012553b64%7D%7B1%7D&wdsectionfileid=6b364628c29feb52%21s1965afa38c4142d88d16f8c0aad11692

75. Circuit Breaker Introduction
https://onedrive.live.com/view.aspx?resid=6B364628C29FEB52%21s9263727369a94fcd83cbce0c0db8053c&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New+Section+1.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FCircuit+Breaker+Fault-Tolerant+Microservice+%28Part-%7Caff21d09-7e7c-4a43-b09c-50e7a2c70e82%2F%29&wdorigin=703&wdpartid=%7B5058ad85-08d9-b107-24e5-0d85cd4fee1d%7D%7B1%7D&wdsectionfileid=6b364628c29feb52%21s1965afa38c4142d88d16f8c0aad11692




@startuml
actor "Upstream System" as Upstream
participant "Kafka Topic\n(instruction.mt304.fx.settle)" as KafkaIn
participant "InboundMt304Flow\n(Spring Integration)" as Flow
participant "AutoFxSettleService" as FXService
database "Database" as DB
participant "Kafka Topic\n(instruction.a4.out.xml.swift.ack)" as KafkaAck
participant "Downstream FX Service" as FXDownstream
participant "Kafka Topic\n(instruction.response.json.inbound.fx.settle)" as KafkaAck
participant "Service Activator\n(processFXSettleInboundResponse)" as RespHandler

== MT304 Inbound==
Upstream -> KafkaIn : Send MT304 (CashInstruction)
KafkaIn -> Flow : Deliver MT304 message

== Processing ==
Flow -> FXService : createInstructionWithMt304(request)
FXService -> DB : Persist MT304 instruction
FXService <- DB : Ack/Result

Flow -> KafkaAck : SEnd CashInstructionAcknowledgement

== Downstream processing ==
FXService -> FXDownstream : (if needed) Trigger FX settlement

FXDownstream -> KakfaResp : Send FXSettleMessageResponse
KafkaResp -> RespHandler : Deliver FX Settle response

RespHandler -> FXService : processFXSettleInboundResponse(response)
FXService -> DB : Update instruction status, etc

@endUml
