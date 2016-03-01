# Add a custom font (montserrat) to your Rails 4.x project

---

Got font from: https://github.com/JulietaUla/Montserrat

Complied fonts at: http://www.fontsquirrel.com

---

1 - Add fonts folder to app/assets:

```ruby
app/assets/fonts
```

2 - Place 'montserrat' folder in the fonts folder:

```ruby
app/assets/fonts/montserrat
```

3 - Create a _fonts.scss file under 'app/assets/stylesheets' and add this:

```ruby
@mixin declare-font-face($path, $font-family, $font-filename, $svg, $font-weight: normal, $font-style: normal) {
  @font-face {
    font-family: '#{$font-family}';
    src: font-url('#{$path}/#{$font-filename}.eot');
    src: font-url('#{$path}/#{$font-filename}.eot?#iefix') format('embedded-opentype'),
         font-url('#{$path}/#{$font-filename}.woff') format('woff'),
         font-url('#{$path}/#{$font-filename}.ttf') format('truetype'),
         font-url('#{$path}/#{$font-filename}.svg##{$svg}') format('svg');
    font-weight: $font-weight;
    font-style: $font-style;
  }
}

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-thin-webfont', 'montserratthin', 100);

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-ultraight-webfont', 'montserratultra_light', 200);
@include declare-font-face('montserrat', 'Montserrat', 'montserrat-light-webfont', 'montserratlight', 300);

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-regular-webfont', 'montserratregular', normal);

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-medium-webfont', 'montserratmedium', 500);

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-semibold-webfont', 'montserratsemi_bold', 600);
@include declare-font-face('montserrat', 'Montserrat', 'montserrat-bold-webfont', 'montserratbold', bold);
@include declare-font-face('montserrat', 'Montserrat', 'montserrat-extrabold-webfont', 'montserratextra_bold', bolder);

@include declare-font-face('montserrat', 'Montserrat', 'montserrat-black-webfont', 'montserratblack', 900);
```

4 - Add your font-family to your body:

```ruby
body {
  font-family: 'Montserrat', sans-serif !important; //had to use !important to override bootstrap
}
```

5 - Precompile assets - add this to 'config/initializers/assets.rb':

```ruby
Rails.application.config.assets.paths << Rails.root.join('app', 'assets', 'fonts')
Rails.application.config.assets.precompile += %w(.svg .eot .woff .ttf)
```

6 - Restart your server and it should work!
