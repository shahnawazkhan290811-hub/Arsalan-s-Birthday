document.addEventListener("DOMContentLoaded", function () {

    /* ================= GET ELEMENTS ================= */

    const pages =
        document.querySelectorAll(".page");

    const nextButton =
        document.getElementById("nextButton");

    const previousButton =
        document.getElementById("previousButton");

    const pageNumber =
        document.getElementById("pageNumber");

    const dotsContainer =
        document.getElementById("dots");


    /* PHOTO MODAL */

    const modal =
        document.getElementById("photoModal");

    const largePhoto =
        document.getElementById("largePhoto");

    const photoCaption =
        document.getElementById("photoCaption");

    const closeButton =
        document.getElementById("closeButton");

    const modalBackground =
        document.querySelector(".modal-background");


    /* CONFETTI */

    const confettiContainer =
        document.getElementById("confetti");


    let currentPage = 0;


    /* ================= CREATE DOTS ================= */

    pages.forEach(function (page, index) {

        const dot =
            document.createElement("button");

        dot.classList.add("dot");

        dot.type = "button";

        dot.setAttribute(
            "aria-label",
            "Go to page " + (index + 1)
        );

        dot.addEventListener(
            "click",
            function () {

                showPage(index);

            }
        );

        dotsContainer.appendChild(dot);

    });


    const dots =
        document.querySelectorAll(".dot");


    /* ================= SHOW PAGE ================= */

    function showPage(index) {

        if (
            index < 0 ||
            index >= pages.length
        ) {
            return;
        }


        currentPage = index;


        /* Hide all pages */

        pages.forEach(function (page, i) {

            if (i === currentPage) {

                page.classList.add("active");

            } else {

                page.classList.remove("active");

            }

        });


        /* Update dots */

        dots.forEach(function (dot, i) {

            if (i === currentPage) {

                dot.classList.add("active");

            } else {

                dot.classList.remove("active");

            }

        });


        /* Update page number */

        pageNumber.textContent =
            (currentPage + 1)
            + " / "
            + pages.length;


        /* Back button */

        previousButton.disabled =
            currentPage === 0;


        /* Next button */

        if (
            currentPage === pages.length - 1
        ) {

            nextButton.textContent =
                "Celebrate! 🎉";

        } else {

            nextButton.textContent =
                "Next Page →";

        }


        window.scrollTo({
            top: 0,
            behavior: "smooth"
        });


        /* Confetti on final page */

        if (
            currentPage === pages.length - 1
        ) {

            createConfetti();

        }

    }


    /* ================= NEXT BUTTON ================= */

    nextButton.addEventListener(
        "click",
        function () {

            if (
                currentPage <
                pages.length - 1
            ) {

                showPage(
                    currentPage + 1
                );

            } else {

                createConfetti();

            }

        }
    );


    /* ================= BACK BUTTON ================= */

    previousButton.addEventListener(
        "click",
        function () {

            if (currentPage > 0) {

                showPage(
                    currentPage - 1
                );

            }

        }
    );


    /* ================= PHOTO POPUP ================= */

    const photoButtons =
        document.querySelectorAll(".photo");


    photoButtons.forEach(function (photo) {

        photo.addEventListener(
            "click",
            function () {

                const image =
                    photo.querySelector("img");

                const caption =
                    photo.getAttribute(
                        "data-caption"
                    );


                largePhoto.src =
                    image.src;


                photoCaption.textContent =
                    caption;


                modal.classList.add("show");

                document.body.style.overflow =
                    "hidden";

            }
        );

    });


    /* ================= CLOSE POPUP ================= */

    function closeModal() {

        modal.classList.remove("show");

        largePhoto.src = "";

        document.body.style.overflow =
            "";

    }


    closeButton.addEventListener(
        "click",
        closeModal
    );


    modalBackground.addEventListener(
        "click",
        closeModal
    );


    /* ================= ESCAPE KEY ================= */

    document.addEventListener(
        "keydown",
        function (event) {

            if (
                event.key === "Escape"
            ) {

                closeModal();

            }


            if (
                event.key === "ArrowRight" &&
                !modal.classList.contains("show")
            ) {

                if (
                    currentPage <
                    pages.length - 1
                ) {

                    showPage(
                        currentPage + 1
                    );

                }

            }


            if (
                event.key === "ArrowLeft" &&
                !modal.classList.contains("show")
            ) {

                if (currentPage > 0) {

                    showPage(
                        currentPage - 1
                    );

                }

            }

        }
    );


    /* ================= CONFETTI ================= */

    function createConfetti() {

        confettiContainer.innerHTML = "";


        const colors = [
            "#ff5fa2",
            "#9b6cff",
            "#ffd166",
            "#73e6c5",
            "#ffffff"
        ];


        for (
            let i = 0;
            i < 80;
            i++
        ) {

            const piece =
                document.createElement("span");


            piece.classList.add(
                "confetti"
            );


            const size =
                Math.random() * 7 + 5;


            const duration =
                Math.random() * 2.5 + 2.5;


            piece.style.left =
                Math.random() * 100 + "%";


            piece.style.width =
                size + "px";


            piece.style.height =
                size * 1.5 + "px";


            piece.style.background =
                colors[
                    Math.floor(
                        Math.random() *
                        colors.length
                    )
                ];


            piece.style.animationDuration =
                duration + "s";


            piece.style.animationDelay =
                Math.random() * .8 + "s";


            piece.style.transform =
                "rotate(" +
                Math.random() * 360 +
                "deg)";


            confettiContainer.appendChild(
                piece
            );

        }


        setTimeout(
            function () {

                confettiContainer.innerHTML =
                    "";

            },
            6000
        );

    }


    /* ================= START WEBSITE ================= */

    showPage(0);

});