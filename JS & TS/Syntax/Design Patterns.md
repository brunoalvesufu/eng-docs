Adotar boas práticas de código e padrões de projeto adequados é essencial para criar software sustentável e de alta qualidade. Aqui estão algumas diretrizes e padrões importantes para desenvolvimento em Node.js e TypeScript:

1. Estilo de Código: Use um linter como ESLint e um formatador como Prettier para manter a consistência do código.
    
    ```bash
    npm install --save-dev eslint prettier
    
    ```
    
    Exemplo de configuração .eslintrc.js:
    
    ```jsx
    module.exports = {
      extends: ['eslint:recommended', 'plugin:@typescript-eslint/recommended'],
      parser: '@typescript-eslint/parser',
      plugins: ['@typescript-eslint'],
      root: true,
    };
    
    ```
    
2. Princípios SOLID:
    
    - Single Responsibility Principle
    - Open/Closed Principle
    - Liskov Substitution Principle
    - Interface Segregation Principle
    - Dependency Inversion Principle
    
    Exemplo de Single Responsibility:
    
    ```tsx
    // Bad
    class User {
      constructor(public name: string) {}
      saveToDatabase() { /* ... */ }
      sendEmail() { /* ... */ }
    }
    
    // Good
    class User {
      constructor(public name: string) {}
    }
    class UserRepository {
      saveUser(user: User) { /* ... */ }
    }
    class EmailService {
      sendEmail(user: User) { /* ... */ }
    }
    
    ```
    
3. Dependency Injection:
    
    ```tsx
    interface Logger {
      log(message: string): void;
    }
    
    class ConsoleLogger implements Logger {
      log(message: string) {
        console.log(message);
      }
    }
    
    class UserService {
      constructor(private logger: Logger) {}
    
      createUser(name: string) {
        // Create user logic
        this.logger.log(`User created: ${name}`);
      }
    }
    
    const logger = new ConsoleLogger();
    const userService = new UserService(logger);
    
    ```
    
4. Repository Pattern:
    
    ```tsx
    interface UserRepository {
      findById(id: number): Promise<User>;
      save(user: User): Promise<void>;
    }
    
    class PostgresUserRepository implements UserRepository {
      async findById(id: number): Promise<User> {
        // Implementation
      }
      async save(user: User): Promise<void> {
        // Implementation
      }
    }
    
    ```
    
5. Factory Pattern:
    
    ```tsx
    interface Animal {
      speak(): void;
    }
    
    class Dog implements Animal {
      speak() { console.log("Woof!"); }
    }
    
    class Cat implements Animal {
      speak() { console.log("Meow!"); }
    }
    
    class AnimalFactory {
      createAnimal(type: string): Animal {
        if (type === "dog") return new Dog();
        if (type === "cat") return new Cat();
        throw new Error("Unknown animal type");
      }
    }
    
    ```
    
6. Singleton Pattern:
    
    ```tsx
    class Database {
      private static instance: Database;
      private constructor() { /* ... */ }
    
      public static getInstance(): Database {
        if (!Database.instance) {
          Database.instance = new Database();
        }
        return Database.instance;
      }
    }
    
    ```
    
7. Observer Pattern:
    
    ```tsx
    interface Observer {
      update(data: any): void;
    }
    
    class Subject {
      private observers: Observer[] = [];
    
      addObserver(observer: Observer) {
        this.observers.push(observer);
      }
    
      notifyObservers(data: any) {
        for (let observer of this.observers) {
          observer.update(data);
        }
      }
    }
    
    ```
    
8. Middleware Pattern (comum em Express.js):
    
    ```tsx
    function authMiddleware(req: Request, res: Response, next: NextFunction) {
      if (req.headers.authorization) {
        next();
      } else {
        res.status(401).send('Unauthorized');
      }
    }
    
    app.use(authMiddleware);
    
    ```
    
9. Error Handling:
    
    ```tsx
    class CustomError extends Error {
      constructor(message: string, public statusCode: number) {
        super(message);
      }
    }
    
    app.use((err: CustomError, req: Request, res: Response, next: NextFunction) => {
      res.status(err.statusCode || 500).json({
        error: {
          message: err.message,
          stack: process.env.NODE_ENV === 'production' ? '🥞' : err.stack,
        },
      });
    });
    
    ```
    
10. Async/Await e Promises: Prefira async/await sobre callbacks para código mais limpo e legível.
    

Estas práticas e padrões ajudam a criar código mais limpo, modular e fácil de manter. A escolha do padrão depende das necessidades específicas do seu projeto.