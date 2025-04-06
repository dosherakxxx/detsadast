
            function highlightCard(id) {
                // Убираем выделение и закрываем описание у всех карточек
                document.querySelectorAll('.clickable-card').forEach(card => {
                    card.classList.remove('expanded-card');
                    card.querySelector('.card-text').classList.add('d-none');
                    const carousel = card.querySelector('.carousel');
                    if (carousel) {
                        carousel.classList.add('d-none');
                    }
                });

                // Прокручиваем к нужной карточке, выделяем её и открываем описание
                const card = document.getElementById(id);
                if (card) {
                    card.scrollIntoView({ behavior: 'smooth', block: 'center' });
                    card.classList.add('expanded-card');
                    card.querySelector('.card-text').classList.remove('d-none');
                    const carousel = card.querySelector('.carousel');
                    if (carousel) {
                        carousel.classList.remove('d-none');
                    }
                }
            }

            function toggleCard(card) {
                const description = card.querySelector('.card-text');
                const carousel = card.querySelector('.carousel');
                if (description.classList.contains('d-none')) {
                    card.classList.add('expanded-card');
                    description.classList.remove('d-none');
                    if (carousel) {
                        carousel.classList.remove('d-none');
                    }
                } else {
                    card.classList.remove('expanded-card');
                    description.classList.add('d-none');
                    if (carousel) {
                        carousel.classList.add('d-none');
                    }
                }
            }

            function searchKindergartens() {
                const query = document.getElementById('searchInput').value.toLowerCase();
                const cards = document.querySelectorAll('#kindergartenCatalog .card');
                cards.forEach(card => {
                    const title = card.querySelector('.card-title').textContent.toLowerCase();
                    if (title.includes(query)) {
                        card.parentElement.style.display = 'block';
                    } else {
                        card.parentElement.style.display = 'none';
                    }
                });
            }

            window.addEventListener('load', () => {
                document.body.classList.add('loaded');
            });
            const backToTop = document.getElementById('backToTop');
            window.addEventListener('scroll', () => {
                if (window.scrollY > 300) {
                    backToTop.style.display = 'flex';
                } else {
                    backToTop.style.display = 'none';
                }
            });
            function scrollToTop() {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }

            function applyFilters() {
                const priceFrom = document.getElementById('priceFrom').value;
                const priceTo = document.getElementById('priceTo').value;
                const district = document.getElementById('districtSelect').value;
                const gardenType = document.getElementById('gardenTypeSelect').value;
                const ages = Array.from(document.querySelectorAll('input[type="checkbox"]:checked')).map(cb => cb.value);

                console.log('Фильтры:', { priceFrom, priceTo, district, gardenType, ages });
                // Здесь можно добавить логику фильтрации карточек
            }

            function sortKindergartens() {
                const sortBy = document.getElementById('sortSelect').value;
                console.log('Сортировка по:', sortBy);
                // Здесь можно добавить логику сортировки карточек
            }

            function resetFilters() {
                document.getElementById('priceFrom').value = '';
                document.getElementById('priceTo').value = '';
                document.getElementById('districtSelect').value = '';
                document.getElementById('gardenTypeSelect').value = '';
                document.querySelectorAll('input[type="checkbox"]').forEach(cb => cb.checked = false);
                document.getElementById('ratingFilter').value = 3;
                document.getElementById('ratingOutput').textContent = 3;
                console.log('Фильтры сброшены');
                // Здесь можно добавить логику сброса фильтров
            }

            function submitReview(event) {
                event.preventDefault();
                const reviewText = document.getElementById('reviewText').value;
                const reviewRating = document.getElementById('reviewRating').value;
                console.log('Отзыв отправлен:', { reviewText, reviewRating });
                // Здесь можно добавить логику отправки отзыва
            }

            function toggleSortByRating() {
                const isChecked = document.getElementById('sortByRatingMain').checked;
                const ratingValue = document.getElementById('ratingFilterMain').value;
                console.log('Сортировка по рейтингу:', isChecked, 'Рейтинг:', ratingValue);
                // Здесь можно добавить логику сортировки карточек по рейтингу
            }
        </script>
    </body>
</html>
