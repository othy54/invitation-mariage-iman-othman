<template>
    <div class="min-h-[100dvh] bg-[#ccb3a3] ">
        <div>
            <div
                class="announ w-full bg-[#ccb3a3] min-h-[100dvh] flex justify-center items-center text-center p-5 leading-[1.5rem] absolute left-0 top-0">
                <img class="absolute w-full h-full object-cover top-0 left-0 opacity-[0.2] mix-blend-overlay"
                    src="/images/bg-isl.jpg" alt="">
                <div>
                    <div class="ann-1 text-[1.4rem]">Ensemble avec leur familles,</div>
                    <div class="ann-1 text-[3.6rem] mt-14 relative">
                        <div class="relative z-[2]">
                            Iman
                        </div>
                        <div
                            class="maghribi absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 opacity-30 text-white">
                            إيمــان
                        </div>
                    </div>
                    <div class="ann-1 text-[2.5rem] leading-[2rem] mt-7 mb-2">&</div>
                    <div class="ann-1 text-[3.6rem] relative">
                        <div class="relative z-[2]">
                            Othman
                        </div>
                        <div
                            class="maghribi absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 opacity-30 text-white">
                            عـثمــان
                        </div>
                    </div>
                    <div class="ann-1 mt-12 text-[1.2rem] leading-[2rem]">Ont la joie de vous convier à leur mariage qui
                        aura
                        lieu
                        le :</div>
                    <div class="ann-1 my-9 text-[3rem] announ__date">
                        2 Août 2025
                    </div>
                    <div class="text-[1.2rem] ann-1">à la mairie de Lunéville à 14h30</div>
                    <div class="mt-8 ann-1">
                        La récéption se tiendra à partir de 18h au
                    </div>
                    <div class="ann-1 mt-1 underline underline-offset-4">
                        <a href="https://www.google.com/maps/place//data=!4m2!3m1!1s0x479480e60cf583df:0xcffa1867a7224163?sa=X&ved=1t:8290&ictx=111"
                            target="_blank">Salon
                            des halles, 1 place Léopold 54300 Lunéville</a>
                    </div>
                </div>
            </div>
            <div
                class="coran text-center bg-[#ccb3a3] w-full min-h-[100dvh] flex justify-center items-center relative p-5 z-[5] absolute left-0 top-0">
                <img class="absolute w-full h-full object-cover top-0 left-0 opacity-[0.3] mix-blend-overlay"
                    src="/images/bg-isl.jpg" alt="">
                <div class="relative">
                    <div class="basmala maghribi text-[1.8rem] w-full text-center">
                        بِسْمِ ٱللَّٰهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ
                    </div>
                    <div class="title maghribi rtl text-center pointer-events-none mt-8">
                        وَمِن ءَايَتِهِۦٓ أَن خَلَقَ لَكُم مِّن أَنفُسِكُم أَزوَجا لِّتَسكُنُواْ إِلَيهَا وَجَعَلَ
                        بَينَكُم
                        مَّوَدَّة وَرَحمَةً إِنَّ فِي ذَٰلِكَ لَأيَت لِّقَوم يَتَفَكَّرُونَ
                    </div>
                </div>
            </div>
            <div
                class="loader w-full min-h-[100dvh] bg-[#ccb3a3] absolute left-0 top-0 p-5 flex justify-center items-center flex flex-col ltr z-10">
                <div>
                    <h1 class="text-white text-center  flex items-center ltr">
                        <span class="splash-i opacity-0 translate-y-[40%]">I</span> <span class="and opacity-0">&</span>
                        <span class="splash-i opacity-0 translate-y-[40%]">O</span>
                    </h1>
                    <div class="date text-center text-2xl text-[#765641] mt-3 opacity-0"> 02.08.2025 </div>
                </div>
                <div class="button mt-16 px-5 py-3 bg-[#765641] text-white cursor-pointer tracking-widest opacity-0">
                    Voir l'invitation
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import SplitType from 'split-type';
import { animate, stagger } from 'motion';

useHead({
    link: [
        {
            rel: 'preload',
            type: 'font/woff2',
            href: '/fonts/maghrib2.woff2',
            as: 'font',
            crossorigin: ''
        }
    ],
    style: [
        `
            @font-face {
                font-family: Maghribi;
                src: url('/fonts/maghrib2.woff2');
                font-display: swap;
                font-weight: 400;
            }
        `
    ]
})

onMounted(() => {

    const quran = new Audio('/audio/coran.mp3');

    new SplitType('.title', { types: 'words,lines' });

    animationLoader();

    quran.addEventListener('ended', () => {
        animate([
            ['.coran', { opacity: 0 }, { duration: 0.8 }],
            ['.ann-1', { opacity: [0, 1], y: [40, 0] }, { duration: 1, delay: stagger(0.2) }]
        ]);

    })

    const button = document.querySelector('.button');

    button.addEventListener('click', () => {
        animate(
            '.loader', { opacity: 0, pointerEvents: 'none' }, {
            duration: 0.8, onUpdate: latest => {
                const words = document.querySelectorAll('.word');
                animate(words, { opacity: [0, 1], y: [55, 0] }, { duration: 10, ease: 'easeOut', delay: stagger(0.5) })
                quran.play();
            }
        }
        )
    })


});

const animationLoader = () => {
    animate([
        ['.splash-i', { opacity: 1, y: [40, 0] }, { duration: 1, delay: stagger(0.3), ease: ['easeOut'] }],
        ['.and', { opacity: 1, y: [40, 0] }, { duration: 1, at: 0.8 }],
        ['.date', { opacity: 1, y: [40, 0] }, { duration: 1, at: 1.5 }],
        ['.button', { opacity: 1 }, { duration: 1 }]
    ]);
};

</script>
<style>
:root {
    --cubic: cubic-bezier(0.66, 0, 0.34, 1);
}

html {
    font-size: calc(16px + 16*(100vw - 320px) / 320);

    @media screen and (min-height: 390px) {
        font-size: calc(16px + 16*(100vw - 390px) / 704)
    }
}

.maghribi {
    font-family: Maghribi;
    direction: rtl;
}

.title {
    font-size: 2rem;
    line-height: 4rem;
}

.word {
    opacity: 0;
    transform: translateY(55%);
}

.loader {
    font-family: Playfair Display;
    background-image: url('/images/arc.png');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;

    & h1 {
        font-size: calc(35vw + 90*(100vw - 390px) / 704);
        line-height: calc(35vw + 90*(100vw - 390px) / 704);

        & .and {
            font-size: 3.6rem;
            margin-inline: -2px;
            position: relative;
            color: #765641
        }

        & span {
            flex: 1;
            display: inline-block;
        }
    }
}

.date {
    letter-spacing: calc(90em / 1000);
}

.announ {
    font-family: Playfair Display;

    & .announ__date {
        font-family: Parisienne;
    }
}
</style>