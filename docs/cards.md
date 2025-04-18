# Scryfall

## API overview and rules
### Endpoint details
- https://api.scryfall.com
- Requests must use HTTPS
- API uses UTF-8 for all responses

### Required Headers
- All requests to api.scryfall.com mus include a `User-Agent` and `Accept` header.
    - For our use, `py {"User-Agent": "BigDecksApp/0.1", "Accept": "*/*"}`

### Use of Scryfall Data and Images
#### Data:
- You may not use Scryfall logos or use the Scryfall name in a way that implies Scryfall has endorsed you, your work, or your product.
- You may not “paywall” access to Scryfall data. You may not require anyone to make payments, take surveys, agree to subscriptions, rate your content, join chat servers, or follow channels in exchange for access to Scryfall data. If you have an account system, end-users should be able to access card data anonymously or with free accounts.
- You may not use Scryfall data to create new games, or to imply the information and images are from any other game besides Magic: The Gathering.
- You may not simply repackage, republish, or proxy Scryfall data. Your software must create additional value for end-users.

#### Images:
- Do not cover, crop, or clip off the copyright or artist name on card images.
- Do not distort, skew, or stretch card images.
- Do not blur, sharpen, desaturate, or color-shift card images.
- Do not add your own watermarks, stamps, or logos to card images.
- Do not place card images in a way that implies someone other than Wizards of the Coast created the card or that it is from another game besides Magic: The Gathering.
- When using the art_crop, list the artist name and copyright elsewhere in the same interface presenting the art crop, or use the full card image elsewhere in the same interface. Users should be able to identify the artist and source of the image somehow.

### Rate Limits and Good Citizenship
- Insert a 100ms between requests to api.scryfall.com (i.e., 10 requests per second).
- *.scryfall.io doesn't have rate limits.
- bulk data is only updated every 24 hours


# Cards

## Strategy
- Get the bulk-data/default-cards json file from api.scryfall.com/bulk-data/default-cards.
    - This gets us the *.scryfall.io URI for the default-cards json file, which means we can avoid worrying about rate limiting.
- Download the default-cards.json and parse the card information in it.
- Store the cards into our db.
- Update every 24 hours or so.

## Cards DB
We're using a subset of the overall information from the Scryfall API, we can always extend to the full amount if necessary.
