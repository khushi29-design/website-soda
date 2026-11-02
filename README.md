# Kwirky website

Next.js 15, TypeScript, Three.js and GSAP.

## Run it
    npm install
    npm run dev        # http://localhost:3000
    npm run build && npm start   # production

## Replace placeholders
| What | Where |
| --- | --- |
| Contact, social links, form endpoints | `src/content/site.ts` |
| Products, flavours, ingredients, prices | `src/content/products.ts` (`confirmed: true` removes the sample sticker) |
| Quiz result to product matches | `productSlug` in `src/content/quiz.ts` |
| FAQ answers | `src/content/faq.ts` |
| Real reviews and team | `src/content/people.ts` |
| Brand story | `src/app/about/page.tsx`, story section in `src/app/page.tsx` |
| Logo | `Wordmark` in `src/components/Bits.tsx` (text stand-in) |
| Can artwork | `labelTexture` in `src/lib/three/can.ts`, stills in `public/cans/` |
| Legal text (drafts, need review) | `src/app/privacy`, `src/app/terms` |

## Connect services
- Forms: set `NEXT_PUBLIC_CONTACT_ENDPOINT` and `NEXT_PUBLIC_NEWSLETTER_ENDPOINT`. Without them, forms open the visitor's email app.
- Payments: implement `CheckoutProvider` in `src/lib/commerce/provider.ts`. Until then, checkout sends a WhatsApp enquiry and takes no money.
- Accounts: the `Customer` type is reserved in `src/lib/commerce/types.ts`; no login exists yet.

## Tests
With the site running on port 3000 and Playwright available:

    NODE_PATH="$(npm root -g)" npm run qa
