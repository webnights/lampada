<template>
    <section class="hero">
        <div class="container">
            <h1 class="title">О нас
              
            </h1>
            <div class="hero__inner">
              
                <div class="hero__content">
                    <p>
                        Ховринская гимназия <strong>«Лампада»</strong> - общеобразовательное частное учебное заведение, основанное в 2009 году при Знаменском храме в Ховрино. Наша цель - сочетание современного прогрессивного обучения и воспитания детей в традициях русской православной культуры. Гимназия Лампада ведет образовательную деятельность уже <strong>более 10 лет</strong>. Лампада имеет государственную лицензию и аккредитацию.
                        <br><br>
                        Здесь в доброжелательной и благочестивой обстановке ученики осваивают образовательные дисциплины, соответствующие федеральному государственному образовательному стандарту (УМК "Школа России"). В качестве конфессиональной составляющей изучаются следующие предметы: Закон Божий, Церковное пение и Церковнославянский язык.
                    </p>
                    <RouterLink to="/products">
                        <Button :content="'Образовательные услуги'" :type="'button'"/>
                    </RouterLink>
                </div>
                <div class="hero__image">
                    <img src="/src/assets/images/hero.jpg">
                </div>
            </div>
        </div>
    </section>
</template>
<script>
    import Button from '/src/components/Button/Button.vue' 
    export default{
        components: {Button},
        methods: {
        scrollToBuses() {
        const busesSection = document.querySelector('.products')
        if (busesSection) {
            busesSection.scrollIntoView({ behavior: 'smooth', alignToTop: true });
        }
        }
    }
    }
</script>
