# L'Élégance

> Timeless fashion for men and women: elegant clothes, shoes and accessories.

## Student
- **Name:** [Your full name]
- **School / Module:** ENSTA - WAMD - TD/TP 2 (React + Redux)

## Application
- **Store name:** L'Élégance
- **Concept:** Online store for classic and elegant fashion for men and women.

## Description
L'Élégance is a small e-commerce frontend built with React.js and Redux Toolkit.
The store sells classic clothing (shirts, trousers, jeans, sweaters), shoes and
accessories (bags, watches, caps) for men and women.

Users can browse the catalog, search for a product, filter by category and
sub-category, add products to a shopping cart, change quantities, remove items
and see the total price in DA (Algerian dinar). The interface updates dynamically
every time the cart changes.

The application has no backend, database, authentication or payment system
(not required for this lab).

## Technologies used
| Technology | Purpose |
|---|---|
| React.js (Vite) | User interface and components |
| JavaScript (ES6+) | Application logic |
| Redux Toolkit | Global state management |
| React-Redux | Connects React components to the Redux store |
| CSS3 | Styling, beige elegant theme, responsive design |
| Google Fonts | Header typography |
| Node.js / npm | Dependencies and dev server |
| Git / GitHub | Version control and submission |

## Project structure
```
ilham-store/
├── public/
│   └── images/            # product pictures
├── src/
│   ├── components/
│   │   ├── Header.jsx
│   │   ├── ProductList.jsx
│   │   ├── ProductCard.jsx
│   │   ├── Cart.jsx
│   │   └── CartItem.jsx
│   ├── redux/
│   │   ├── store.js
│   │   └── cartSlice.js
│   ├── data/
│   │   └── products.js
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── index.html
└── package.json
```

## Main React components
| Component | Role | Props / State |
|---|---|---|
| `App` | Root component, assembles the page | local state `showCart` |
| `Header` | Logo, store tagline and cart button with item counter | prop `onToggleCart`, reads Redux |
| `ProductList` | Search bar, category filters and product grid | local state `search`, `group`, `sub` |
| `ProductCard` | Displays one product (image, name, price) with an "Add to cart" button | prop `product`, dispatches `addToCart` |
| `Cart` | Lists cart items, shows the total and a "Clear cart" button | reads Redux, dispatches `clearCart` |
| `CartItem` | One cart line with quantity buttons and a remove button | prop `item`, dispatches Redux actions |

## Redux state managed by the application
The global state is created with Redux Toolkit (`createSlice`) in `src/redux/cartSlice.js`
and registered in `src/redux/store.js`.

```js
state.cart = {
  items: [
    { id, name, group, category, price, image, quantity }
  ]
}
```

**Actions**
| Action | Effect |
|---|---|
| `addToCart(product)` | Adds the product, or increases its quantity if already in the cart |
| `removeFromCart(id)` | Removes the product from the cart |
| `increaseQuantity(id)` | Quantity + 1 |
| `decreaseQuantity(id)` | Quantity - 1 (minimum 1) |
| `clearCart()` | Empties the cart |

**React-Redux usage**
- `<Provider store={store}>` wraps the app in `main.jsx`
- `useSelector` reads the cart (`Header`, `Cart`)
- `useDispatch` sends actions (`ProductCard`, `CartItem`, `Cart`)

## Local state (useState)
- `showCart` in `App`: show or hide the cart
- `search`, `group`, `sub` in `ProductList`: search text and active filters

## Implemented features
- Product catalog with images, names, categories and prices in DA
- Add to cart and remove from cart
- Quantity management (+ / -)
- Cart total updated in real time
- Clear cart
- Cart counter in the header
- Product search
- Category filters: Clothes, Shoes, Accessories
- Sub-categories: Men / Women (Clothes, Shoes) and Bags / Jewelry / Others (Accessories)
- Custom logo, header typography and beige color theme
- Responsive layout (desktop and mobile)

## How to run the application
Requirements: Node.js and npm installed.

```bash
git clone [your-repository-link]
cd ilham-store
npm install
npm run dev
```

Then open the address shown in the terminal, usually `http://localhost:5173/`.

To create a production build:
```bash
npm run build
```
