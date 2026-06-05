# Booking.com - Release notes
## Version 3.2
>
>**Release Date:** 26 May 2026
>
>**Document Version:** 1.1
>
>**Prepared by:** Vidhya

---

## Overview

Booking.com API v3.2 introduces new APIs, enhancements to existing payment services, and bug fixes designed to improve partner onboarding, payment processing, and reservation management.

These release notes are intended for:

- API partners
- Connectivity providers
- Property management system (PMS) providers
- Developers integrating with Booking.com APIs

## What's new

###  New API: Payments by Booking Onboarding API

Payments by Booking Onboarding API enables you to check whether a property is eligible for Payments by Booking, submit onboarding requests with preferred payout settings, track request status, and receive status update notifications.

To learn more and start using it, see the Payments by Booking Onboarding API documentation.

###  New API: Payments by Credit Card Status API

Credit Card Status API enables you to check the validity of credit cards for "Pay at property" reservations and take action when a card is invalid.

To learn more and start using it, see the Credit Card Status API documentation.

###  New API: New Property Deal Promotions API 

New Property Deal enables you to create a new promotion type in the existing Promotions API for eligible new properties that have been open and bookable on Booking.com for less than 12 months and have no reservations yet.

To learn more and start using it, see the Creating a new property deal.

## Improvements

### Payments API New version v1.1 for multiple endpoints

To provide a more detailed breakdown of partner payouts, commissions, charges, and reservation payment information while remaining backward compatible.

**Key highlights**

- As of June 1st 2026, the Payments API uses 1.1 as the latest version by default when the accept-version header is not provided.
- Providers can keep the v1.0 behavior by passing the accept-version: 1.0 request header.
- The partner_payout.commissions_and_charges.breakdown object separates total_commissions and total_charges.
- Charge items in price_breakdown[].charges[] include applicable_rate when a base rate is available.
- Charge items in price_breakdown[].charges[] include applicable_type to show how a charge applies to a reservation, for example PER_PERSON or PER_NIGHT.
- The response includes payment_tags to indicate the payment type and collection method for a reservation.
- Bank transfer payout details include bank_transfer_reference to help identify and track a payout.

## Known Issues

There are no known issues in this release.

## Fixed Issues

| ID | Severity | Description |
|----|----------|-------------|
| ACI-4588 | Medium | Fixed incorrect ACK alert emails. |
| ACI-4586 | High | Resolved JWT validation failures that caused 401 errors. |



  *This sample release notes document was created for portfolio purposes using publicly available product updates. The content has been reorganized and rewritten to demonstrate technical writing, information architecture, and release communication skills.*
