---
layout: post
title: "Building a Full-Stack Restaurant Ordering Platform with React and Node.js"
date: 2024-11-05
author: "Mason"
tags: ["React", "Node.js", "Full-Stack", "Tutorial"]
---

In this post, I'll share insights from building PeerCafe, a comprehensive restaurant ordering platform that demonstrates modern full-stack development practices.

## Project Overview

PeerCafe is a multi-tenant platform where users can discover restaurants, browse menus, place orders, and track deliveries. The platform also includes an admin dashboard for restaurant owners to manage their operations.

## Architecture Decisions

### Frontend Stack
- **React with Next.js**: Provides server-side rendering, static generation, and excellent developer experience
- **TypeScript**: Adds type safety and catches errors early
- **Tailwind CSS + Material-UI**: For responsive, professional UI components
- **React Context API**: Manages global state like shopping cart

### Backend Stack
- **Node.js with Express**: Lightweight and perfect for RESTful APIs
- **PostgreSQL**: Robust relational database for complex queries
- **Supabase**: Managed PostgreSQL with built-in authentication
- **Docker**: Containerization for consistent deployment

## Key Challenges & Solutions

### Challenge 1: Real-time Order Updates
**Problem**: Users need live order status updates without constant polling.

**Solution**: Implemented WebSocket connections for push notifications on order status changes.

```javascript
// Example WebSocket connection
const socket = io('https://api.peercafe.com');
socket.on('order-status-update', (data) => {
  updateOrderUI(data.order_id, data.status);
});
```

### Challenge 2: Complex Database Queries
**Problem**: Retrieving restaurant data with filtered menus and availability.

**Solution**: Optimized queries with proper indexing and JOIN operations.

```sql
SELECT r.*, 
       array_agg(mi.item_name) as menu_items
FROM restaurants r
LEFT JOIN menu_items mi ON r.id = mi.restaurant_id
WHERE r.is_active = true
GROUP BY r.id;
```

### Challenge 3: Testing Complex Interactions
**Problem**: Testing user workflows involving multiple components and API calls.

**Solution**: Comprehensive test suite using Jest and React Testing Library with proper mocking.

```typescript
it('should complete checkout process successfully', async () => {
  const { user } = renderWithProviders(<CheckoutPage />);
  
  await user.type(screen.getByLabelText(/email/i), 'user@example.com');
  await user.click(screen.getByRole('button', { name: /place order/i }));
  
  await waitFor(() => {
    expect(mockCart.clearCart).toHaveBeenCalled();
  });
});
```

## Best Practices Implemented

1. **Clean Code**: Following SOLID principles and maintainable code structure
2. **Error Handling**: Comprehensive error handling with user-friendly messages
3. **Security**: Input validation, CORS configuration, and secure authentication
4. **Performance**: Database query optimization, caching strategies
5. **Testing**: Unit tests, integration tests, and component tests
6. **Documentation**: Clear README files and inline code comments

## Lessons Learned

1. **Start with architecture**: Planning the database schema and API design upfront saved significant refactoring later
2. **Test early**: Writing tests during development, not after, catches bugs faster
3. **User feedback**: Regular testing with actual users revealed UX issues
4. **Performance matters**: Query optimization made a huge difference in load times

## Future Improvements

- [ ] Payment integration for real transactions
- [ ] Machine learning for restaurant recommendations
- [ ] Mobile app with React Native
- [ ] Real-time chat with restaurants
- [ ] Advanced analytics dashboard

## Conclusion

Building PeerCafe was an excellent opportunity to practice full-stack development with modern technologies. The combination of React, Node.js, and PostgreSQL proved to be a powerful and flexible stack.

Feel free to check out the [GitHub repository](https://github.com/kaotickoopa/peercafe) for the complete code!

---

Have questions or suggestions? Let me know in the comments below!
