### Installation

1. Clone the repo
   ```sh
   https://github.com/jameslara090/YWA-HUMAN-RESOURCES-WEBSITE.git
   ```
2. Go to project directory
   ```cmd
   cd YWA-HUMAN-RESOURCES-WEBSITE
   ```
3. Install PHP dependencies
   ```sh
   composer install
   ```
4. Install NPM packages
   ```sh
   npm install
   ```
5. Create your `.env` or you can create a copy of the predefined environment sample
   ```sh
   cp .env.example .env
   ```
6. Generate your `APP_KEY`
   ```php
   php artisan key:generate
   ```
7. Create database tables and seed migrations
   ```php
   php artisan migrate:fresh --seed
   ```
8. Symlink storage for image public path
   ```php
   php artisan storage:link
   ```
   
### Serve App for `development`

1. backend
   ```php
   php artisan serve
   ```
2. frontend
   ```sh
   npm run watch
   ```
3. (`optional`) If has problem with php cache always run:
   ```php
   php artisan optimize:clear
   ```
   
<p align="right">(<a href="#top">back to top</a>)</p>
