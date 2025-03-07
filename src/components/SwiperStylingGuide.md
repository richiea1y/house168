# Swiper Styling Guide

This guide helps you understand how to style different parts of the Swiper component in your Vue project.

## Main Components

### 1. Main Container
```css
.swiper {
  /* Container styling */
  width: 100%;
  height: 400px; /* Adjust height as needed */
  padding: 20px;
  background-color: #f5f5f5;
}
```

### 2. Slide Wrapper & Slides
```css
.swiper-wrapper {
  /* Wrapper styling */
  align-items: center;
}

.swiper-slide {
  /* Individual slide styling */
  text-align: center;
  height: auto; /* For equal height slides */
  
  /* Center slide contents */
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### 3. Navigation Buttons
```css
.swiper-button-prev,
.swiper-button-next {
  /* Button styling */
  background-color: white;
  color: #333;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  
  /* Icon styling - the arrow itself */
  &::after {
    font-size: 18px;
  }
  
  /* Positioning adjustments */
  top: 50%; /* Vertical position */
}

/* Specific positioning */
.swiper-button-prev {
  left: 10px;
}

.swiper-button-next {
  right: 10px;
}
```

### 4. Pagination
```css
.swiper-pagination {
  /* Pagination container */
  bottom: 10px; /* Distance from bottom */
}

.swiper-pagination-bullet {
  /* Individual pagination dot */
  background: #666;
  opacity: 0.5;
  width: 8px;
  height: 8px;
  margin: 0 4px;
  
  /* Active bullet */
  &.swiper-pagination-bullet-active {
    opacity: 1;
    background: #333;
    /* For elongated active bullet */
    width: 20px; 
    border-radius: 5px;
  }
}
```

## Common Customizations

### Fade Effect for Slides
```css
.swiper-slide {
  opacity: 0.4;
  transition: opacity 0.3s;
  
  &.swiper-slide-active {
    opacity: 1;
  }
}
```

### Scale Effect for Slides
```css
.swiper-slide {
  transform: scale(0.8);
  transition: transform 0.3s;
  
  &.swiper-slide-active {
    transform: scale(1);
  }
}
```

### Centering Active Slide
For your Swiper component:
```html
<swiper
  :centered-slides="true"
  ...other props
>
```

### Hiding Navigation or Pagination Conditionally
```css
@media (max-width: 768px) {
  .swiper-button-prev,
  .swiper-button-next {
    display: none;
  }
}
``` 