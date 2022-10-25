# Recognize Change Notification Action

This action consists of a composite set of actions that allow you to be notified when a certain file or directory
within your repository changes. Currently, this action only supports email notifications. You can specify a connection
string that will be used to send the email. The connection string should be a secret in your repository.

## Example
```yaml
on:
  push:
    branches:
      - develop

jobs:
  check-changes:
    runs-on: ubuntu-latest
    steps:
      - uses: recognizegroup/recognize-change-notification-action@v1
        with:
          notification-type: email # Type of notification
          path: src/file # The path to the file or directory that should be checked for changes
          mail-connection-url: ${{ secrets.SMTP_CONNECTION_STRING }} # The connection string to use to send the email (smtp+starttls://user:password@server:port, smtp://user:password@server:port)
          mail-subject: File Changed # The subject of the email
          mail-from-name: Example # The from name of the email
          mail-from-address: info@example.com # The from address of the email
          mail-to: info@example.com, admin@example.com # The to address of the email, separated by commas
```
