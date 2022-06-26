# Free Emailing

Use:
 - [Gmail](https://gmail.com/)
 - [Google Domains](https://domains.google.com/)

To get:
 - Free emailing with your custom domain. (E.g. `hello@my-domain.com`.)
 - Free emailing with a programmatic JavaScipt API. (More reliable than SaaS like [mailgun](https://www.mailgun.com/).)

Yes, you read right: all this for free. (Except for your domain registration costs, obviously.)

> This setup does *not* use Google Workspaces (which has no free tier anymore).


## Custom Domain Emailing

> IIRC, there is a soft cap of sending 500 emails per day. PR welcome if I'm wrong, or to add an information source if I'm right.

1. If your domain, e.g. `my-domain.com`, is not already registered with [Google Domains](https://domains.google.com/), then transfer your domain to Google Domains [domains.google.com/registrar/transfer](https://domains.google.com/registrar/transfer).
   >  - Google Domains will show you some transfer cost, but these are only one additional domain year purchase. Transferring is actually free.
   >  - Transfer takes [Takes 5-7 days](https://support.google.com/domains/answer/9003220?hl=en&ref_topic=9003137).
1. After transfer is done, set up email forwarding in Google Domains to forward all `*@my-domain.com` to your Gmail account e.g. `my-email@gmail.com`: [domains.google.com/registrar/](https://domains.google.com/registrar/) > My domains [my-domain.com] > Manage > Email > Email forwarding > Add email alias.
1. Test your domain setup.
   - Create a new temporary fake Gmail account: Go to [gmail.com](https://gmail.com) in Incognito Mode (`<Ctrl><Shift>N`).
     > - No telephone number nor secondary email is required (a Gmail account can be created completely anonymously).
     > - The are a zillions of disposable emails services, such as [guerrillamail.com](https://www.guerrillamail.com), but these are not reliable. In the end, it's just faster to quickly create a new Gmail account.


## Programmatic Emailing

> Programmatic emailing means, for example, to send emails from JavaScipt `sendEmail({ from: 'hello@my-domain.com', to: 'some-customer@hotmail.com', subject: 'hello', body: 'Regarding your last email...' })`.

For programmatic emailing with JavaScript and [Nodemailer](https://github.com/nodemailer/nodemailer):
 - [Stack Overflow > What is the definitive way to use Gmail with OAuth and Nodemailer? > Accepted Answer](https://stackoverflow.com/questions/51933601/what-is-the-definitive-way-to-use-gmail-with-oauth-and-nodemailer/51933602#51933602)

You can now send emails from `hello@my-domain.com` with JavaScript.

> More infos about using Gmail with Nodemailer:
> - [Google > site:stackoverflow.com nodemailer gmail](https://www.google.com/search?q=site%3Astackoverflow.com+nodemailer+gmail)
> - [Google > site:stackoverflow.com nodemailer gmail oauth](https://www.google.com/search?q=site%3Astackoverflow.com+nodemailer+gmail+oauth)
