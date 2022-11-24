# Strapi

## Development mode

- first, make sure you have a correct setup database (prefer same type as production like postgres)
- make your change on db structure with dev mode : `yarn develop`

## Push to production

This project is deploy on heroku with his own postgres DB.

Your DB structure will be copy in production by pushing your code on heroku with : 
`git push heroku HEAD:main`