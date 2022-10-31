# Free Emailing

Use:
 - [Gmail](https://gmail.com/)
 - [Google Domains](https://domains.google.com/)

To get:
 - Free emailing with your custom domain. (E.g. `hello@my-domain.com`.)
 - Free emailing with a programmatic JavaScipt API. (More reliable than SaaS like [mailgun](https://www.mailgun.com/).)

Yes, you read right: all this for free. (Except for your domain registration costs, obviously.)

> This setup does *not* use Google Workspaces (which has no free tier anymore).

> IIRC, there is a soft cap of sending 500 emails per day. PR welcome if I'm wrong, or, if I'm right, to add an information source.
> If you want to go beyond that limit, you'll have to use a service like mailgun. (Gmail doesn't have any paid plan to increase that limit.)

## Custom Domain Emailing

1. If your domain, e.g. `my-domain.com`, is not already registered with [Google Domains](https://domains.google.com/), then transfer your domain to Google Domains [domains.google.com/registrar/transfer](https://domains.google.com/registrar/transfer).
   > Google Domains will show you some transfer cost, but these are only one additional domain year purchase. Transferring is actually free.

   > Transfer takes [Takes 5-7 days](https://support.google.com/domains/answer/9003220?hl=en&ref_topic=9003137).
1. Create a Gmail account, e.g. `my-email@gmail.com`, if you don't have one already.
1. After transfer is done, set up email forwarding in Google Domains to forward all `*@my-domain.com` to your Gmail email.
   - Go to: [domains.google.com/registrar/](https://domains.google.com/registrar/) > My domains > `my-domain.com` > Manage > Email > Email forwarding > Add email alias. Then add `*@my-domain.com` with the forward target `my-email@gmail.com`.
1. Setup up a new `Send email as` configuration in your Gmail to enable sending emails from `hello@my-domain.com` using your gmail account `my-email@gmail.com`.
   1. Generate app password:
      1. Go to [`Google Account` > `Security`](https://myaccount.google.com/security?hl=en) > `App passwords`.
      1. Set `Select app` to `Other (custom name)` > Set name to something like `Send email as hello@my-domain.com`.
      1. Click `Generate` > Save app password somewhere safe.
   2. In the Gmail settings of `my-email@gmail.com`:
      1. Go to [`Settings` > `Accounts and Import`](https://mail.google.com/mail/u/0/#settings/accounts).
      1. In the section `Send mail as` click link `Add another email address` and fill:
         - `Email address` => `hello@my-domain.com`
         - `Treat as an alias` => `yes`
         - `SMTP Server` => `smtp.gmail.com`
         - `Port` => `587`
         - `Username` => `my-email` (the account name of `my-email@gmail.com`)
         - `Password` => the app password generated in the previous step
         - `Secured connection using TLS (recommended)` => `yes`
      1. Enter the verification code, which you received in your gmail
1. Test your setup.
   - Create a new temporary fake Gmail account: Go to [gmail.com](https://gmail.com) in Incognito Mode (`<Ctrl><Shift>N`).
     > No telephone number nor secondary email is required (a Gmail account can be created completely anonymously).

     > The are a zillions of disposable emails services, such as [guerrillamail.com](https://www.guerrillamail.com), but these are not reliable. In the end, it's just faster to quickly create a new Gmail account.


## Programmatic Emailing

> Programmatic emailing means, for example, to send emails from JavaScipt `sendEmail({ from: 'hello@my-domain.com', to: 'some-customer@hotmail.com', subject: 'You got a new message', body: 'Someone replied to your post...' })`.

For programmatic emailing with JavaScript and [Nodemailer](https://github.com/nodemailer/nodemailer):
 - [Stack Overflow > What is the definitive way to use Gmail with OAuth and Nodemailer? > Accepted Answer](https://stackoverflow.com/questions/51933601/what-is-the-definitive-way-to-use-gmail-with-oauth-and-nodemailer/51933602#51933602)

You can now send emails from `hello@my-domain.com` with JavaScript.

> More infos about using Gmail with Nodemailer:
> - [Google > site:stackoverflow.com nodemailer gmail](https://www.google.com/search?q=site%3Astackoverflow.com+nodemailer+gmail)
> - [Google > site:stackoverflow.com nodemailer gmail oauth](https://www.google.com/search?q=site%3Astackoverflow.com+nodemailer+gmail+oauth)
