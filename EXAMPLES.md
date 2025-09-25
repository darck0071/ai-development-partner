# 🎮 Real-World Examples

## 📋 Laravel CRUD Generation

**Input:**
```
Create CRUD for Product management with categories
```

**AI Response:**
```
🎯 КРАТКИЙ АНАЛИЗ ЗАДАЧИ
Создание полноценного CRUD для управления продуктами с категориями. 
Нужно учесть связи many-to-many, валидацию, API документацию и права доступа.

⚡ ПЛАН РЕАЛИЗАЦИИ
1. Модели Product + Category с pivot-таблицей
2. API контроллеры с полной валидацией  
3. Swagger документация
4. Базовые тесты

⚠️ РИСКИ: При большом каталоге нужны будут индексы и кэширование

🛠 КОМАНДЫ ДЛЯ ТЕРМИНАЛА
php artisan make:model Product -mcr
php artisan make:model Category -mc
php artisan make:request ProductRequest
...
```

[Full example with complete code →](examples/laravel-crud-complete.md)

---

## 💰 Business Feature Analysis

**Input:**
```
Add subscription billing to our SaaS platform
```

**AI Response:**
```
🎯 КРАТКИЙ АНАЛИЗ ЗАДАЧИ
Подписочная модель для SaaS - критически важная функция для монетизации.
Нужно учесть: планы подписок, пробный период, автопродление, failed payments.

💼 БИЗНЕС-АНАЛИЗ:
- Потенциальный MRR: +200-500k/мес при conversion 2-5%
- Требует интеграции с payment gateway (Stripe/PayPal)
- Необходима email-автоматизация для retention

⚡ ПЛАН РЕАЛИЗАЦИИ:
1. Subscription management система
2. Webhook обработка платежей
3. Trial period логика
4. Dunning management
5. Analytics dashboard

🔒 БЕЗОПАСНОСТЬ:
- PCI DSS compliance через Stripe
- Защита webhook endpoints
- Audit trail для всех transactions
```

[Full business analysis example →](examples/saas-subscription-analysis.md)

---

## 🔧 Code Review Example

**Input:**
```php
public function getUserOrders($userId) {
    $orders = DB::select("SELECT * FROM orders WHERE user_id = $userId");
    return $orders;
}
```

**AI Response:**
```
⚠️ КРИТИЧЕСКИЕ ПРОБЛЕМЫ:

🔐 БЕЗОПАСНОСТЬ: SQL Injection уязвимость!
📊 ПРОИЗВОДИТЕЛЬНОСТЬ: N+1 проблема при связанных данных
🏗️ АРХИТЕКТУРА: Нарушение принципов Laravel

🛠 ИСПРАВЛЕННАЯ ВЕРСИЯ:

public function getUserOrders(int $userId): Collection 
{
    return Order::with(['items', 'status'])
        ->where('user_id', $userId)
        ->latest()
        ->get();
}

✅ УЛУЧШЕНИЯ:
- Eloquent ORM защищает от SQL инъекций
- Eager loading предотвращает N+1
- Type hints для безопасности типов  
- Возвращает Collection вместо array
```

---

## 🚀 DevOps Infrastructure Setup

**Input:**
```
Setup production environment for Laravel app
```

**AI Response:**
```
🎯 АНАЛИЗ ИНФРАСТРУКТУРЫ
Настройка production среды требует учета: масштабируемости, 
безопасности, мониторинга, backup стратегии.

🏗️ АРХИТЕКТУРА:
- Load Balancer (Nginx)
- App Servers (PHP-FPM)  
- Database (MySQL Master-Slave)
- Cache (Redis)
- Queue (Redis/SQS)
- File Storage (S3)

📋 ЧЕКЛИСТ БЕЗОПАСНОСТИ:
✅ SSL certificates (Let's Encrypt)
✅ Firewall rules (UFW)
✅ Database encryption
✅ Environment variables protection
✅ Regular security updates

🔍 МОНИТОРИНГ:
- Application: Laravel Telescope
- Server: New Relic / DataDog
- Logs: ELK Stack
- Uptime: Pingdom
```

[Complete DevOps setup guide →](examples/production-setup-guide.md)

---

## 🎨 Frontend Integration Example

**Input:**
```
Create React component for product catalog with search
```

**AI Response:**
```
🎯 АНАЛИЗ UX/UI ТРЕБОВАНИЙ
Каталог продуктов - ключевая страница для конверсии.
Нужно: поиск, фильтры, пагинация, responsive дизайн.

💡 UX РЕКОМЕНДАЦИИ:
- Поиск с автодополнением (debounce 300ms)
- Фильтры в sidebar с количеством результатов
- Infinite scroll или pagination
- Loading states и skeleton screens

⚡ ТЕХНИЧЕСКАЯ РЕАЛИЗАЦИЯ:
- React Query для caching API calls
- Debounced search hooks
- URL state management для SEO
- Lazy loading изображений

🧪 A/B ТЕСТ ИДЕИ:
- Grid vs List view по умолчанию
- Фильтры слева vs сверху  
- Количество товаров на странице
```

---

## 📱 API Documentation Example

**Input:**
```
Document user authentication API
```

**AI Response:**
```
📝 SWAGGER ДОКУМЕНТАЦИЯ

Полная OpenAPI 3.0 спецификация включает:
- Все endpoints (login, register, refresh, logout)
- Request/Response schemas
- Error codes с примерами
- Security schemes (Bearer token)
- Rate limiting информация

🔐 БЕЗОПАСНОСТЬ:
- Password complexity требования
- Rate limiting: 5 requests/minute для login
- JWT token expiration: 1 hour
- Refresh token: 30 days

📊 МОНИТОРИНГ:
- Failed login attempts tracking
- Session management dashboard
- Security audit logs
```

[Complete API documentation →](examples/api-auth-swagger.json)

---

## 🧪 Testing Strategy Example

**Input:**
```
Create testing strategy for e-commerce checkout
```

**AI Response:**
```
🧪 КОМПЛЕКСНАЯ СТРАТЕГИЯ ТЕСТИРОВАНИЯ

📋 УРОВНИ ТЕСТИРОВАНИЯ:
1. Unit Tests (70%): Individual components
2. Integration Tests (20%): API endpoints  
3. E2E Tests (10%): Critical user journeys

🛒 CHECKOUT FLOW TEST CASES:
✅ Happy path: successful purchase
✅ Invalid payment method
✅ Inventory insufficient  
✅ Network timeout scenarios
✅ Concurrent purchase attempts
✅ Tax calculation accuracy
✅ Shipping options validation

🔄 АВТОМАТИЗАЦИЯ:
- CI/CD pipeline integration
- Parallel test execution
- Test data factories
- Mock external services

📊 COVERAGE TARGET: 90%+ для critical paths
```

## 💬 How to Use These Examples

1. **Copy the system prompt** to your AI assistant
2. **Try similar inputs** with your own projects
3. **Adapt the responses** to your specific tech stack
4. **Share your results** in GitHub Discussions

## 🤝 Contributing Examples

Have a great example? Please contribute:
1. Fork the repository
2. Add your example to this file
3. Submit a Pull Request
4. Include before/after comparison

---

**More examples coming soon:**
- Mobile app development
- Microservices architecture  
- Database optimization
- Security audit checklist
- Performance monitoring setup
