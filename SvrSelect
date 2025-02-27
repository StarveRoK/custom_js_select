
class SvrSelect {
    constructor(user_value, user_values, user_icon) {
        this.default_svg = '<svg class="bi bi-caret-left-fill" fill="currentColor" height="12" viewBox="0 0 16 16" width="12" xmlns="http://www.w3.org/2000/svg"><path d="m3.86 8.753 5.482 4.796c.646.566 1.658.106 1.658-.753V3.204a1 1 0 0 0-1.659-.753l-5.48 4.796a1 1 0 0 0 0 1.506z"></path></svg>';
        this.value = user_value;
        this.values = user_values;
        this.icon = user_icon || user_icon === false ? user_icon : this.default_svg;
        this.icon_div = '';

        const div = document.createElement('div');
        div.classList.add('svr-select-main-container');

        const top_div = document.createElement('div');
        top_div.classList.add('svr-select-top-div');
        top_div.setAttribute('data-value', this.value['val'] ? this.value['val'] : '');
        div.appendChild(top_div);
        this.top_div = top_div;

        const bot_div = document.createElement('div');
        bot_div.classList.add('svr-select-bot-div');
        div.appendChild(bot_div);
        bot_div.style.display = 'none';

        const value_span = document.createElement('span');
        value_span.classList.add('svr-span-value');
        value_span.innerHTML = this.value['name'] ? this.value['name'] : 'Выбрать из списка';
        top_div.appendChild(value_span);

        if(this.icon && this.icon !== false){
            const icon_div = document.createElement('div');
            icon_div.classList.add('svr-icon-div');
            if(this.default_svg === this.icon){;
                icon_div.classList.add('rotate');
            }
            icon_div.innerHTML = this.icon;
            top_div.appendChild(icon_div);
            this.icon_div = icon_div;
        }

        this.values.forEach((val) => {
            const values_div = document.createElement('div');
            values_div.classList.add('svr-values-div');
            values_div.setAttribute('data-value', val['val']);
            if(val['val'] === this.value['val']){ values_div.classList.add('active'); }

            const values_span = document.createElement('span');
            values_span.classList.add('svr-span-values');
            values_span.innerHTML = val['name'];
            values_div.appendChild(values_span);
            bot_div.appendChild(values_div);

            values_div.addEventListener('click', () => {
                top_div.setAttribute('data-value', val['val']);
                value_span.innerHTML = val['name'];
                Array.from(div.querySelectorAll('.svr-values-div.active')).forEach((e) => {
                    e.classList.remove('active');
                })
                values_div.classList.add('active');
            })
        })

        this.div = div;

        div.addEventListener('click', () => {
            const rect = bot_div.getBoundingClientRect();
            if (
                rect.x === 0 &&
                rect.y === 0 &&
                rect.width === 0 &&
                rect.height === 0
            ){
                bot_div.style.display = 'flex';
                const height = bot_div.clientHeight;
                bot_div.style.minHeight = '0';
                bot_div.style.height = '0';

                let step = Math.round(height / 20);
                let height_now = 0;
                let interval = setInterval(() => {
                    bot_div.style.height = height_now + 'px';
                    height_now += step;
                    if(height_now >= height){
                        bot_div.style.height = height + 'px';
                        clearInterval(interval);
                    }
                },5)

                if(this.icon && this.icon !== false){
                    this.icon_div.classList.remove('close');
                    this.icon_div.classList.add('open');
                }

            } else {
                if(this.icon && this.icon !== false){
                    this.icon_div.classList.remove('open');
                    this.icon_div.classList.add('close');
                }

                const height = bot_div.clientHeight;
                let step = Math.round(height / 20);
                let height_now = height;
                let interval = setInterval(() => {
                    if(height_now <= 0){
                        clearInterval(interval);
                        bot_div.removeAttribute('style');
                        bot_div.style.display = 'none';
                    }
                    bot_div.style.height = height_now + 'px';
                    height_now -= step;
                },5)
            }
        })
    }

    append_in(selector) {
        const el = document.querySelector(selector);
        el.appendChild(this.div);
    }

    get_select(selector) {
        return this.div;
    }

    get_value(){
        return this.top_div.getAttribute('data-value');
    }
}
