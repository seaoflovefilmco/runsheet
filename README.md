# runsheet

The Sea of Love wedding-day runsheet form. Couples receive a
personalised link with their Monday item ID and fill in their
wedding details across six steps.

Lives at `runsheet.seaoflove.com.au`.

## Architecture

Single static `index.html` with embedded CSS and JS. No build
step, no dependencies. Deploys via GitHub Pages from `main`.

On submit, the form POSTs a JSON payload to a Make.com webhook
which routes the data to the matching project row on a Monday
board. The Monday item ID is supplied via the `id` URL parameter
(e.g. `?id=1234567890&couple=Amy%20%26%20Braden`).

## Configuration

Swap `WEBHOOK_URL` near the top of the `<script>` block once the
Make scenario is live. Until then, submits surface a graceful
error message and keep the form state intact.

## Drafts

State persists to `localStorage` under `runsheet:<mondayItemId>`
on every input change, and is cleared on successful submit.
