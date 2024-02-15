# General Structure
This ad format is a JSON object designed to provide a detailed overview of digital advertising campaigns. It contains several key sections, each representing different aspects of the ad, such as campaign details, advertiser information, creative content, targeting strategy, financials, moderation status, and additional platform-specific parameters.

## 1. Campaign Identification (`campaign_id`)
- **Field**: `campaign_id`
- **Type**: String
- **Description**: A unique identifier for the advertising campaign. It's crucial for tracking the campaign across different platforms.
- **Example**: `"CMP1122334455"`

## 2. Advertiser Information (`advertiser`)
This section offers comprehensive details about the entity responsible for the ad.

- **Field**: `advertiser`
- **Type**: Object
- **Description**: Contains the advertiser's ID, name, location, legal name of the funding entity, and VAT number.
- **Structure**:
  - `advertiser_id` (String): Unique identifier of the advertiser.
  - `advertiser_name` (String): Name of the advertiser.
  - `advertiser_location` (String): Geographical location of the advertiser.
  - `funder_legal_name` (String): Legal name of the entity funding the ad.
  - `funder_vat` (String): VAT number of the funding entity.
- **Example**:
  ```json
  "advertiser": {
    "advertiser_id": "ADV987654321",
    "advertiser_name": "EcoFriendly",
    "advertiser_location": "Paris, France",
    "funder_legal_name": "EcoFriendly Products S.A.R.L.",
    "funder_vat": "FR123456789"
  }
  ```

## 3. Creative Content (`creative`)
This array contains details of each creative element in the campaign.

- **Field**: `creative`
- **Type**: Array of Objects
- **Description**: Each object in the array represents a creative asset used in the ad, such as an image or video.
- **Structure**:
  - `creative_id` (String): A unique identifier for each creative.
  - `creative_type` (String): The type of creative (e.g., "Carousel").
  - `creative_title` (String): Title of the creative.
  - `creative_description` (String): Description of the creative.
  - `creative_media_urls` (Array of Strings): URLs linking to the creative media.
  - `creative_action` (Object): Describes the intended action, including the objective, destination URL, caption, and title.
  - `interactions` (Object): Engagement metrics, such as clicks, impressions, and engagements.
- **Example**:
  ```json
  "creative": [
    {
      "creative_id": "CREA998872537999",
      "creative_type": "Carousel",
      "creative_title": "Sustainable Living Solutions",
      "creative_description": "Discover our range of eco-friendly home products.",
      "creative_media_urls": [
        "https://example.com/image.jpg",
        "https://example.com/image1.jpg"
      ],
      "creative_action": {
        "objective": "Website Traffic",
        "destination_url": "https://www.ecofriendlyproducts.com",
        "caption": "ecofriendlyproducts.com",
        "title": "Eco Friendly Products Home"
      },
      "interactions": {
        "clicks": 1500,
        "impressions": 30000,
        "engagements": [
          {"type": "Likes", "count": 250},
          {"type": "Comments", "count": 40}
        ]
      }
    }
  ]
  ```

## 4. Targeting (`targeting`)
This section outlines the ad's audience targeting strategy, segmented by geography and demographics.

- **Field**: `targeting`
- **Type**: Object
- **Description**: Contains detailed targeting information, organized by country, region, and demographic groups.
- **Structure**:
  - Country and region names as keys.
  - Each region contains demographic segments (e.g., `Male`, `Female`) with age groups.
  - Each demographic segment includes `reach`, `impressions`, `languages`, `first_shown_date`, and `last_shown_date`.
- **Example**:
  ```json
  "targeting": {
    "FR": {
      "Île-de-France": {
        "Male": { "18-24": { /* reach, impressions, etc. */ } },
        "Female": { "25-34": { /* reach, impressions, etc. */ } },
        "languages": ["French"],
        "first_shown_date": "2024-05-01",
        "last_shown_date": "2024-05-15"
      },
      // Additional regions...
    },
    // Additional countries...
  }
  ```

## 5. Payments (`payments`)
Details the financial aspects of the ad campaign.

- **Field**: `payments`
- **Type**: Object
- **Description**: Includes the actual and expected costs of the campaign, along with the currency.
- **Structure**:
  - `campaign_actual_cost` (String): The actual cost range of the campaign.
  - `campaign_expected_total_cost` (String): The expected total cost range.
  - `campaign_payment_currency` (String): The currency used for the campaign costs.
- **Example**:
  ```json
  "payments": {
    "campaign_actual_cost": "100-500",
    "campaign_expected_total_cost": "1000-2500",
    "campaign_payment_currency": "EUR"
  }
  ```

## 6. Moderation (`moderation`)
Reflects the ad's compliance with platform policies.

- **Field**: `moderation`
- **Type**: Object
- **Description**: Contains the moderation status and history of decisions.
- **Structure**:
  - `status` (String): The current status of the ad (e.g., "Approved").
  - `moderation_decision` (Array of Objects): Each object details a decision, including the date and decision type.
- **Example**:
  ```json
  "moderation": {
    "status": "Approved",
    "moderation_decision": [
      {"date": "2024-04-30", "decision": "Approved"}
    ]
  }
  ```

## 7. Parameters (`parameters`)
An open field for additional, platform-specific data.

- **Field**: `parameters`
- **Type**: Object
- **Description**: Allows platforms to add any necessary, unique data to complement the existing format.
- **Usage**: Can include data like audience interests, behavior metrics, etc.
- **Example**:
  ```json
  "parameters": {
    "keywords": ["eco-friendly", "ecology"]
  }
  ```

This detailed documentation should serve as a guide for developers and stakeholders to understand and implement the proposed ad format. It aims to ensure clarity and consistency while offering flexibility for platform-specific adaptations.
