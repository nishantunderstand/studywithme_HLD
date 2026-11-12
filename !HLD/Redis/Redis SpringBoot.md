SpringBoot-Redis 
	1. Approach 1 — Spring Cache abstraction
	2. Approach 2 — Direct Redis operations


Spring Boot Caching Basics (@Cacheable, @CachePut, @CacheEvict)
```java
@CachePut(value = "users", key = "#user.id")
public User updateUser(User user) {
    return userRepository.save(user);
}
```

- Redis in Spring Boot
- @Cacheable
- @CachePut
- @CacheEvict
- How to enable it ?
- Pom.xml Dependency name 
- How does @Cacheable actually work?


Redis 
Two Approaches
```
              Your Service
                   |
              @Cacheable
                   |
                   v
          Spring Cache Abstraction
                   |
       +-----------+-----------+
       |                       |
   Caffeine                  Redis
       |                       |
   Local Cache            Distributed Cache
```

