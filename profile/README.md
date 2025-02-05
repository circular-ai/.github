# ⚡ Circular AI Powered Resale ⚡

## Stack
1. Next.js
2. Vercel for hosting, with seperate deployment for /test
3. Supabase as auth and database
4. Drizzle as ORM `+`
5. TanStack for state
6. ShadCN as framework
7. Vercel AI SDK

`+` to be implemented

![Architecture](https://github.com/justchrister/circular/blob/54e460041e632fdd452e7c5528d83fafad65cfd6/architecture.png)


## Repo

ℹ️ This is not currently fully implemented, and work-in-progress

```bash
circular-ai/
├── app/
│   ├── (admin)/                # Circular admin tools
│   │   ├── layout.tsx
│   ├── (app)/
│   │   ├── organizations/
│   │   │   └── [subdomain]/
│   │   │       ├── deliveries/
│   │   │       ├── payouts/
│   │   │       ├── products/
│   │   │       ├── sellers/
│   │   │       ├── settings/
│   │   │       └── page.tsx     # Shows either store management or seller experience depending on the user role.
│   │   ├── actions.tsx
│   │   └── layout.tsx
│   ├── (docs)/
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── (home)/                           
│   │   ├── store-management/
│   │   │   └── page.tsx
│   │   ├── seller-experience/
│   │   │   └── page.tsx
│   │   ├── ... more pages
│   │   ├── layout.tsx
│   │   └── index.tsx
│   ├── api/
│   │   ├── [organzationSlug]/
│   │   └── platform/
│   └── contexts/
├── components/
│   ├── app/                     # store management and seller experience components
│   │   ├── auth/
│   │   ├── store-management/
│   │   │   ├── action-bar/
│   │   │   │   ├── filters/
│   │   │   │   └── ...
│   │   │   ├── contextual-command/
│   │   │   ├── metrics/
│   │   │   ├── settings/
│   │   │   ├── sheets/
│   │   │   ├── sidebar/
│   │   │   └── tables/
│   │   └── seller-experience/
│   ├── home/
│   ├── docs/
│   └── ui/                     # primitive reusable UI components
├── utils/                      # general-purpose, reusable functions that are not tied to a specific domain.
│   ├── services/
│   ├── products/
│   ├── organizations/
│   └── ...
├── public/
├── types/                  
│   ├── services/
│   │   └── products/
│   │   └── organizations/
│   │   └── ...
│   └── ...
└── lib/
```

## Intro

Main parts of the app are:

**The app** (`org`.getcircular.ai)

Organizations are our customers, each organization has their own subdomain. On this subdomain we deliver both the store management and the seller experience.
- **Store management**  where the coworkers that work in the thrift-stores use on a day-to-day basis, to add and manage their products as well as their relationship with the sellers.
- **Seller experience** Is where the sellers (the people that sell products via the thrift-stores or rent racks to sell products) can see the current status of their products, request payouts, book deliveries, and more.

**Docs** (getcircular.ai/docs)

This is where we deliver the documentation for the product.

**Homepage** (getcircular.ai)

The content-rich website, where we gather leads and showcase the product.

## Services

All services are built in a microservice pattern, where the functions should offer standard interfaces to interact with them. 

ℹ️ Using stores as an example throughout this documentation.

1. They have a general route at `/api/[org]/stores` (as well as more granular ones, such as `/api/[org]/stores/delivery-schedule`)
3. All DB actions are in utils folder [/utils/services/service-stores](/utils/services/service-stores).
They should be split by logical actions, such as `getStoreDeliverySchedule` and `updateStoreDeliveryConfig`.
5. In Next we have corresponding hooks w/ reactQuery 

## Roadmap

⚡ Implement first customer feature requirements
- ~~configurable business model, flows, and seller experience~~
- sellers to add products to deliveries
- integrate with 3 x POS

⚡ ~~Integrate pricing assistant MVP in create flow~~

⚡ Pay down technical debt: 
- react query (in progress)
- drizzle (in progress)
- improve database structure (in progress)
- proper ci/cd (in progress)
- proper API routes (in progress)

⚡ Multi-step product classification 
- ~~pic of product (get category and color)~~
- pic of label x 2 (get material, brand, and material)

✨ 
