<template>
    <header class="main-header">
        <div class="container">
            <div class="header-content">
                <img src="@/assets/images/logo.svg" alt="Logo">
                <div class="user-interface">
                    <div class="user-info">
                        <p class="user-name">Светлана</p>
                        <p class="user-role">Сотрудник</p>
                    </div>
                    <div class="user-avatar">
                        <img src="@/assets/images/user-avatar.jpg" alt="">
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {

}
</script>

<style lang="css">
.main-header {
    background-color: var(--white);
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.header-content {
    display: flex;
    justify-content: space-between;
    padding: 20px 0;
}

.user-interface {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: var(--font-size-4);
}

.user-name {
    color: var(--blue);
    font-weight: bold;
}
</style>