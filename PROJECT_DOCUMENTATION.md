# Shopizer Admin - Project Documentation

## Overview

Shopizer Admin is an Angular-based web application that serves as the administrative interface for the Shopizer e-commerce platform. It provides comprehensive management capabilities for online stores, including catalog management, order processing, customer management, and store configuration.

## Technology Stack

- **Framework**: Angular 11.2.14
- **UI Library**: Nebular 5.0.0 / 6.2.0
- **Bootstrap**: 4.3.1
- **Node Version**: v12.22.7
- **Angular CLI**: 13.3.x
- **TypeScript**: 4.0.8
- **Charts**: Chart.js, ngx-charts, echarts
- **Internationalization**: @ngx-translate
- **Date Handling**: date-fns, moment
- **Rich Text Editor**: Summernote, Quill
- **File Management**: ng6-file-man, ngx-awesome-uploader

## Project Structure

```
shopizer-admin/
├── src/
│   ├── app/
│   │   ├── @core/           # Core services and utilities
│   │   ├── @theme/          # UI theme components and styles
│   │   ├── pages/           # Feature modules
│   │   │   ├── auth/        # Authentication (login, register, password reset)
│   │   │   ├── catalogue/   # Product catalog management
│   │   │   ├── content/     # Content management (pages, images, files)
│   │   │   ├── customers/   # Customer management
│   │   │   ├── home/        # Dashboard
│   │   │   ├── orders/      # Order management
│   │   │   ├── payment/     # Payment configuration
│   │   │   ├── shipping/    # Shipping configuration
│   │   │   ├── store-management/  # Store settings and configuration
│   │   │   ├── tax-management/    # Tax configuration
│   │   │   ├── user-management/   # User and permissions management
│   │   │   └── shared/      # Shared components, services, guards
│   │   ├── app.module.ts
│   │   └── app-routing.module.ts
│   ├── assets/              # Static assets (images, i18n, styles)
│   ├── environments/        # Environment configurations
│   └── index.html
├── docker/                  # Docker configuration
├── conf/                    # Nginx configuration
├── e2e/                     # End-to-end tests
└── package.json
```

## Key Features

### 1. **Authentication & Authorization**
- Login/logout functionality
- Password reset and recovery
- User registration
- Role-based access control (Superadmin, Admin, Admin Retail, Admin Catalogue, Admin Order, Admin Content, Customer)

### 2. **Catalog Management**
- Product management (create, edit, delete)
- Category management
- Product options and variants
- Product types
- Brand management
- Product groups
- Catalog organization

### 3. **Order Management**
- Order listing and search
- Order details view
- Order history tracking
- Order invoicing
- Transaction management

### 4. **Customer Management**
- Customer listing and profiles
- Customer options and attributes
- Customer credentials management
- Custom customer fields

### 5. **Store Management**
- Store creation and configuration
- Store details and branding
- Multi-store support
- Retailer management
- Store landing pages

### 6. **Content Management**
- Page management
- Image management
- File uploads
- Content boxes
- Promotional content

### 7. **Shipping Configuration**
- Shipping methods
- Shipping rules
- Package configuration
- Origin settings
- Shipping rates

### 8. **Payment Configuration**
- Payment method setup
- Payment gateway configuration
- Custom payment forms

### 9. **Tax Management**
- Tax class configuration
- Tax rate management

### 10. **User Management**
- User creation and profiles
- Permission management
- Password changes
- User roles assignment

## Application Modes

The application supports three operational modes (configured in `environment.ts`):

1. **STANDARD**: Single store mode
2. **MARKETPLACE**: Multi-vendor marketplace with global categories
3. **BTB**: Business-to-business mode

## Configuration

### Environment Variables

Located in `src/environments/environment.ts`:

```typescript
{
  production: false,
  googleApiKey: '',
  mode: 'STANDARD',  // MARKETPLACE | BTB | STANDARD
  apiUrl: "http://localhost:8080/api",
  shippingApi: 'http://localhost:9090/shipping/api/v1',
  client: {
    language: {
      default: 'en',
      array: ['fr', 'en']
    }
  }
}
```

### Backend API

The application connects to a Shopizer backend API. Default configuration:
- **API URL**: `http://localhost:8080/api`
- **Shipping API**: `http://localhost:9090/shipping/api/v1`

## Installation & Setup

### Prerequisites
- Node.js v12.22.7
- Angular CLI 13.3.x

### Local Development

```bash
# Install dependencies
npm install --legacy-peer-deps

# Start development server
ng serve -o

# Access application
http://localhost:4200
```

### Build for Production

```bash
ng build
```

### Docker Deployment

```bash
docker run \
  -e "APP_BASE_URL=http://localhost:9090/api" \
  -it --rm -p 4200:80 shopizerecomm/shopizer-admin
```

## Default Credentials

- **Username**: admin@shopizer.com
- **Password**: password

## Key Dependencies

### UI & Styling
- **@nebular/theme**: Modern Angular UI framework
- **@ng-bootstrap/ng-bootstrap**: Bootstrap components
- **eva-icons**: Icon library
- **roboto-fontface**: Typography

### Data Visualization
- **chart.js**: Chart rendering
- **@swimlane/ngx-charts**: Angular chart components
- **ngx-echarts**: Apache ECharts integration

### Forms & Input
- **angular2-query-builder**: Dynamic query builder
- **ng-multiselect-dropdown**: Multi-select dropdowns
- **ngx-summernote**: Rich text editor
- **libphonenumber-js**: Phone number validation

### File Management
- **ng6-file-man**: File manager component
- **ngx-awesome-uploader**: File upload
- **ngx-dropzone**: Drag-and-drop file upload
- **fine-uploader**: Advanced file uploading

### Utilities
- **@ngx-translate**: Internationalization
- **ngx-toastr**: Toast notifications
- **rxjs**: Reactive programming
- **date-fns**: Date manipulation

## Security Features

- JWT-based authentication
- HTTP interceptors for auth tokens
- Role-based access control
- Route guards for protected pages
- Global error handling

## Internationalization

Supports multiple languages with default English and French:
- Translation files in `src/assets/i18n/`
- Language switching capability
- Configurable default language

## Testing

```bash
# Unit tests
npm test

# Test coverage
npm run test:coverage

# E2E tests
npm run e2e

# Linting
npm run lint
npm run lint:styles
```

## Development Scripts

```bash
npm start              # Start dev server
npm run build          # Production build
npm run lint:fix       # Auto-fix linting issues
npm run docs           # Generate documentation
npm run docs:serve     # Serve documentation
```

## Browser Support

Configured in `browserslist`:
- Modern browsers (last 2 versions)
- Chrome, Firefox, Safari, Edge
- iOS Safari
- Android Chrome

## License

MIT License - Copyright (c) 2017 akveo.com

## Additional Notes

- Uses legacy peer dependencies for compatibility
- Includes custom scrollbar styling (malihu-custom-scrollbar)
- Supports Google Maps integration
- Includes Leaflet for mapping features
- Smart tables with ng2-smart-table
- Modal dialogs with ngx-smart-modal
- Image lightbox with ngx-lightbox
